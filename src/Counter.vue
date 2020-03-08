<template>
  <div>
    <h2>カウンター</h2>
    <div>{{ countMessage }}</div>
    <button @click="count++">Click me!</button>
    <button @click="count = 0">Reset</button>
  </div>
</template>

<script>
export default {
  name: "counter",
  data() {
    return {
      count: 0
    };
  },
  computed: {
    countMessage() {
      return "回数: " + this.count;
    }
  }
};
</script>

<style></style>
