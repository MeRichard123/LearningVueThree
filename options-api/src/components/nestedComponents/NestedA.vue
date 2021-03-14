<template>
  <div>
    <h2>Component A</h2>
    <NestedB />
  </div>
</template>

<script>
import NestedB from "./NestedB";
export default {
  components: {
    NestedB,
  },
};
</script>

<style lang="scss" scoped></style>
