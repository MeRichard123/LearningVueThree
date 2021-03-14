<template>
  <div class="main">
    <h1>Options - {{ o_firstname }}</h1>
    <!-- Don't need .value vue unpacks automatically -->
    <h1>Composition - {{ c_firstname }}</h1>
    <p>{{ greet }}</p>
    <p>{{ greetHero }}</p>
  </div>
</template>

<script>
import { ref } from "vue";

// We can use the options api and the composition API together
export default {
  name: "Data",
  //   Composition API uses the setup function
  setup() {
    // Ref is data and takes an initial value, use ref to create a reactive reference
    // Returns a reactive mutable object
    const c_firstname = ref("Bob");
    const c_lastname = ref("Ross");
    // Mutate state
    c_firstname.value = "Daniel";
    const greet = `Hello ${c_firstname.value}`;
    console.log(c_firstname);
    const greetHero = `Hello ${c_firstname.value} ${c_lastname.value}`;

    // To use in a template we return from setup
    return {
      c_firstname,
      greet,
      greetHero,
    };
  },
  data() {
    return {
      o_firstname: "Richard",
    };
  },
};
</script>

<style scoped>
.main {
  padding: 50px;
  background-color: cornflowerblue;
}
</style>
