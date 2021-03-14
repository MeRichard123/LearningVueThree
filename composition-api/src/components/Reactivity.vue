<template>
  <div>
    {{ name }}
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  name: "Reactivity",
  setup() {
    // Doing this will not update the template, Ref reacts upon changes
    // let name = "Richard";
    // setTimeout(() => {
    //   name = "RichardMe123";
    // }, 2000);

    const name = ref("Richard");

    setTimeout(() => {
      name.value = "RichardMe123";
    }, 2000);

    return {
      name,
    };
  },
};
</script>

<style scoped></style>
