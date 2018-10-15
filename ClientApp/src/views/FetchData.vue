<template>
    <div>
    <h1>Weather forecast</h1>
    <p>This component demonstrates fetching data from the server.</p>
    <p v-if="!forecasts"><em>Loading...</em></p>
    <table class="table" v-if="forecasts">
        <thead>
            <tr>
                <td>Date</td>
                <td>Temp. (C)</td>
                <td>Temp. (F)</td>
                <td>Summary</td>
            </tr>
        </thead>
        <tbody>
            <tr v-for="forecast of forecasts" :key="forecast.dateFormatted">
                <td>{{ forecast.dateFormatted }}</td>
                <td>{{ forecast.temperatureC }}</td>
                <td>{{ forecast.temperatureF }}</td>
                <td>{{ forecast.summary }}</td>
            </tr>
        </tbody>
    </table>
    </div>
</template>
<script lang="ts">
import axios from "axios";
import Vue from "vue";

interface IWeatherForecast {
  dateFormatted: string;
  temperatureC: number;
  temperatureF: number;
  summary: string;
}

function getBaseUrl() {
  return document.getElementsByTagName("base")[0].href;
}

export default Vue.extend({
  data() {
    return {
      forecasts: [] as any
    };
  },

  methods: {
    fetchData: function() {
      let url = `${getBaseUrl()}api/SampleData/WeatherForecasts`;
      axios
        .get(url)
        .then(result => (this.forecasts = result && result.data))
        // eslint-disable-next-line
        .catch(error => console.error(error));
    }
  },

  created: function() {
    this.fetchData();
  }
});
</script>
<style lang="scss">
</style>
