<template>
  <div>
    <h2>This is a Pop Up</h2>
    <input type="text" v-model="name" />
    <!-- Emit event to parent, first is the event emit and second is data-->
    <button @click="$emit('close', name)">Close Pop Up</button>
  </div>
</template>

<script>
// Custom events are used to pass data upwards to the parent
// Allow children to communicate with their parent
export default {
  name: "CustomEvents",
  // emits: ['close']   methods to emit
  // an emit object allow you to add validation functions they take the data prop as a param
  emits: {
    close: (name) => {
      if (!name) {
        return false;
      } else {
        return true;
      }
    },
  },
  data() {
    return {
      name: "",
    };
  },
};
</script>

<style scoped></style>
