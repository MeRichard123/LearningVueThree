<template lang="">
  <h2>Methods</h2>
  <p>Addition: {{ add(2, 3, 5) }}</p>
  <p>Multiply: {{ multiply(10) }}</p>
</template>
<script>
export default {
  name: "Methods",
  data() {
    return {
      baseMultiplier: 5,
    };
  },
  methods: {
    add(a, b, c) {
      return a + b + c;
    },
    // Access data property with 'this' keywords
    multiply(num) {
      return this.baseMultiplier * num;
    },
  },
};
</script>
<style lang=""></style>
