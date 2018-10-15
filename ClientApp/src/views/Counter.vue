<template>
    <div>
        <h1>Counter</h1>
        <p>This is a simple example of an Vue component.</p>
        <p>Current count: <strong>{{ currentCount }}</strong></p>
        <button @click="incrementCounter()">Increment</button>
    </div>
</template>

<script lang="ts">
import Vue from "vue";

export default Vue.extend({
  data: function() {
    return {
      currentCount: 0
    };
  },

  methods: {
    incrementCounter() {
      this.currentCount++;
    }
  }
});
</script>