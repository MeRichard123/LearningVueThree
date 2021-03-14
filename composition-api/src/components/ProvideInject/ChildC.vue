<template>
  <div>
    <h2>Child C --> {{ userName }}</h2>
    <p>Composition Username {{ childUsername }}</p>
    <p>Reactive {{ childAge }} - {{ firstName }} {{ lastName }}</p>
    <button @click="changeVals">Change In Child</button>
  </div>
</template>

<script>
import { inject, toRefs } from "vue";
export default {
  name: "ChildC",
  setup() {
    const childUsername = inject("c_username", "Default Username");
    const childAge = inject("c_age", 0);
    const childPerson = inject("c_person", { None: "404" });
    const changeVals = inject("changeVals");

    return {
      childUsername,
      childAge,
      ...toRefs(childPerson),
      changeVals,
    };
  },
  inject: ["userName"],
};
</script>

<style scoped></style>
