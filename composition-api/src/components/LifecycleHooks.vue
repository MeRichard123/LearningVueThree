<template>
  <div></div>
</template>

<script>
/*
    Options vs Composition
    beforeCreate, created = not needs -> setup()
    beforeMount = onBeforeMount
    beforeUpdate = onBeforeUpdate 
    etc...
    */
import {
  onBeforeUnmount,
  onMounted,
  onBeforeUpdate,
  onUpdated,
  onBeforeMount,
  onUnmounted,
} from "vue";
export default {
  name: "LifecycleHooks",
  setup() {
    onBeforeUnmount(() => {
      console.log("Before Unmount");
    });
    onMounted(() => {
      console.log("Mounted");
    });
    onBeforeUpdate(() => {
      console.log("Before Update");
    });
    onUpdated(() => {
      console.log("Updated");
    });
    onBeforeMount(() => {
      console.log("Before Mount");
    });
    onUnmounted(() => {
      console.log("Unmounted");
    });
  },
};
</script>

<style scoped></style>
