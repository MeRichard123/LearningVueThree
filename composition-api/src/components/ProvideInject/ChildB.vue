<template>
  <div>
    <h2>Child B</h2>
    <ChildC />
  </div>
</template>

<script>
import ChildC from "./ChildC";
export default {
  components: {
    ChildC,
  },
};
</script>

<style scoped></style>
