<template>
  <div>
    <h2>{{ count }}</h2>
    <button @click="increment">Increment Count</button>
    <p>{{ firstName }} {{ lastName }}</p>
    <button @click="changeHero">Change Hero</button>
  </div>
</template>

<script>
import { ref, reactive, toRefs } from "vue";
export default {
  name: "Methods",
  setup() {
    const count = ref(0);

    const increment = () => {
      count.value++;
    };
    const state = reactive({
      firstName: "Jakub",
      lastName: "Coric",
    });

    const changeHero = () => {
      state.firstName = "Dead";
      state.lastName = "Pool";
    };

    return {
      count,
      increment,
      ...toRefs(state),
      changeHero,
    };
  },
};
</script>

<style lang="scss" scoped></style>
