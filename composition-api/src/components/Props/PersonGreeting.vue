<template>
  <div>
    <p>Hello {{ fullName }}</p>
    <button @click="sendEvent">Send Event to Parent</button>
  </div>
</template>

<script>
import { computed } from "vue";
export default {
  name: "PersonGreeting",
  props: ["firstName", "lastName"],
  setup(props, context) {
    const fullName = computed(() => {
      // To use props pass props
      return `${props.firstName} ${props.lastName}`;
    });

    // setup takes second argument context which can be emit custom events
    const sendEvent = () => {
      console.log("Emitting", context);
      context.emit("callHeros", fullName.value);
    };

    return {
      fullName,
      sendEvent,
    };
  },
  emits: ["callHeros"],
};
</script>

<style scoped></style>
