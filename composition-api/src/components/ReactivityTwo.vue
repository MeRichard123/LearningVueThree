<template>
  <div>
    <h5>{{ firstName }} {{ lastName }}</h5>
  </div>
</template>

<script>
import { reactive, toRefs } from "vue";
export default {
  name: "ReactvityTwo",
  setup() {
    //   Have to access it with state.
    const state = reactive({
      firstName: "Bruce",
      lastName: "Wayne",
    });
    // if we return like this
    //   return {
    //      firstName: state.firstName,
    //      lastName: state.lastName,
    // };
    // This will not update in the UI because we saved the variable
    // in return and vue will only react to the sate property
    // to fix this use the toRefs() function
    setTimeout(() => {
      state.firstName = "Clark";
      state.lastName = "Kent";
    }, 2000);
    console.log(state);

    // so that we don't have to use state. in template
    // We can directly return the attributes
    //   return {
    //      firstName: state.firstName,
    //      lastName: state.lastName,
    // };
    // The toRefs function will preserve reactivity.
    return toRefs(state);
  },
};
</script>

<style lang="scss" scoped></style>
