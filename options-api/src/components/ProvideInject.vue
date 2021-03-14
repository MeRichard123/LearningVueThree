<template>
  <div>
    <NestedA />
  </div>
</template>

<script>
// Provide and Inject is like react Context
import NestedA from "./nestedComponents/NestedA";
export default {
  components: {
    NestedA,
  },
};
</script>

<style scoped></style>
