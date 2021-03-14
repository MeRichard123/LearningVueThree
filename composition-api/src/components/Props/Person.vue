<template>
  <div>
    <input type="text" placeholder="firstname" v-model="firstName" />
    <input type="text" placeholder="lastName" v-model="lastName" />

    <PersonGreeting
      :firstName="firstName"
      :lastName="lastName"
      @callHeros="call"
    />
  </div>
</template>

<script>
import { ref } from "vue";
import PersonGreeting from "./PersonGreeting";
export default {
  name: "Person",
  components: {
    PersonGreeting,
  },
  setup() {
    const firstName = ref("");
    const lastName = ref("");

    const call = (hero) => {
      console.log("Hi");
      alert(`Calling ${hero}`);
    };

    return {
      firstName,
      lastName,
      call,
    };
  },
};
</script>

<style scoped></style>
