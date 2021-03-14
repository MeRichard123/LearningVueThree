<template>
  <div>
    <h2>Child Component</h2>
  </div>
</template>

<script>
export default {
  name: "Child",
  beforeCreate() {
    console.log("Child beforeCreate()");
  },
  created() {
    console.log("Child created()");
  },
  beforeMount() {
    console.log("Child beforeMount()");
  },
  mounted() {
    console.log("Child Mounted()");
  },
  beforeUpdate() {
    console.log("Child beforeUpdate()");
  },
  updated() {
    console.log("Child unmounted()");
  },
  beforeUnmount() {
    console.log("Child beforeUnmount()");
  },
  unmounted() {
    console.log("Child unmounted()");
  },
};
</script>

<style scoped></style>
