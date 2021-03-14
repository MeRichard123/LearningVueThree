<template>
  <div class="main">
    <h3>Parent Component --> {{ name }}</h3>
    <p>{{ age }} - {{ firstName }} {{ lastName }}</p>
    <button @click="changeVals">Change Values</button>
    <ChildA />
  </div>
</template>

<script>
import { provide, ref, reactive, toRefs } from "vue";
import ChildA from "./ChildA";

export default {
  name: "ProvideInject",
  components: { ChildA },
  setup() {
    const age = ref("17");
    const person = reactive({
      firstName: "Bruce",
      lastName: "Wayne",
    });

    const changeVals = () => {
      age.value++;
      person.lastName = "Wayne!";
    };
    // See ChildC for inject
    provide("c_username", "Data From Main");
    provide("c_age", age);
    provide("c_person", person);
    provide("changeVals", changeVals);

    return {
      age,
      ...toRefs(person),
      changeVals,
    };
  },
  data() {
    return {
      name: "Richard",
    };
  },
  provide() {
    return {
      userName: this.name,
    };
  },
};
</script>

<style scoped>
.main {
  padding: 50px;
  background-color: darksalmon;
}
</style>
