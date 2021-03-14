<template>
  <div>Hello {{ name }}, age {{ personAge }}</div>
</template>

<script>
export default {
  // Passing Props - define an array with the name of props
  name: "PropComponent",
  props: ["name", "personAge"],
};
</script>

<style scoped></style>
