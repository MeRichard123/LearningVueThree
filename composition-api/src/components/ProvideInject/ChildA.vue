<template>
  <div>
    <h2>Child A</h2>
    <ChildB />
  </div>
</template>

<script>
import ChildB from "./ChildB";
export default {
  name: "ChildA",
  components: {
    ChildB,
  },
};
</script>

<style scoped></style>
