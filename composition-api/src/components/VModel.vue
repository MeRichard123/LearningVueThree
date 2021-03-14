<template>
  <div class="main">
    <ul>
      <li>{{ firstName }}</li>
      <li>{{ lastName }}</li>
      <li>{{ heroname }}</li>
    </ul>
    <input type="text" placeholder="First Name" v-model="firstName" />
    <input type="text" placeholder="Last Name" v-model="lastName" />
    <input type="text" placeholder="Hero Name" v-model="heroname" />
  </div>
</template>

<script>
import { ref, reactive, toRefs } from "vue";
export default {
  name: "VModel",
  setup() {
    const heroname = ref("");
    const state = reactive({
      firstName: "",
      lastName: "",
    });

    return {
      heroname,
      ...toRefs(state),
    };
  },
};
</script>

<style scoped>
.main {
  padding: 50px;
  background-color: aquamarine;
}
</style>
