<template>
  <div>Component B - {{ username }}</div>
</template>

<script>
export default {
  name: "NestedB",
  inject: ["username"],
};
</script>

<style lang="scss" scoped></style>
