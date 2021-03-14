<template>
  <div class="Main">
    <h1>Options API</h1>
    <input type="text" placeholder="Name" v-model="name" />
    <h2>{{ firstName }} {{ lastName }}</h2>
    <input type="text" placeholder="Ref FirstName" v-model="firstName" />
    <input type="text" placeholder="Ref LastName" v-model="lastName" />
    <h2>Composition Reactive</h2>
    <input type="text" placeholder="Reactive FirstName" v-model="fName" />
    <input type="text" placeholder="Reactive LastName" v-model="lName" />
    <input
      type="text"
      placeholder="Reactive Deep Hair Colour"
      v-model="options.hairColour"
    />
  </div>
</template>

<script>
import { ref, watch, reactive, toRefs } from "vue";
import _ from "lodash";

export default {
  name: "Watchers",
  setup() {
    const firstName = ref("");
    const lastName = ref("Harry");

    //! watching one
    // watch(firstName, (newVal, oldVal) => {
    //   console.log("Old Value", oldVal);
    //   console.log("New Value", newVal);
    // });
    // ?Watching multiple
    // ?Setting Immediate will run on render
    watch(
      [firstName, lastName],
      (newVals, oldVals) => {
        console.log("First Name Old Value", oldVals[0]);
        console.log("First Name New Value", newVals[0]);

        console.log("Last Name Old Value", oldVals[1]);
        console.log("Last Name New Value", newVals[1]);
      },
      { immediate: true }
    );

    //! Using Reactive

    const state = reactive({
      fName: "",
      lName: "",
      options: {
        hairColour: "",
      },
    });

    //! Watching reactive - old and new values will be the same
    // watch(state, (newValue, oldVal) => {
    //   console.log("fName Old Value", oldVal.fName);
    //   console.log("fName New Value", newValue.fName);

    //   console.log("lName Old Value", oldVal.lName);
    //   console.log("lName New Value", newValue.lName);
    // });
    //! To watch separately we pass a getter and spread the reactive prop
    watch(
      () => {
        return { ...state };
      },
      (newValue, oldVal) => {
        console.log("fName Old Value", oldVal.fName);
        console.log("fName New Value", newValue.fName);

        console.log("lName Old Value", oldVal.lName);
        console.log("lName New Value", newValue.lName);
      }
    );
    //! If we only wanted to watch one prop we would specify it as a getter
    //  ()=> {return state.fName}

    //! Watching Deeply nested props
    //! This will set the old value to the new value we need to make a deep copy
    watch(
      () => {
        _.cloneDeep(state.options);
      },
      (newValue, oldVal) => {
        console.log("Hair Old Value", oldVal);
        console.log("Hair New Value", newValue);
      },
      { deep: true }
    );

    return {
      firstName,
      lastName,
      ...toRefs(state),
    };
  },

  //!   Options
  data() {
    return {
      name: "",
    };
  },
  watch: {
    name(newVal, oldVal) {
      console.log("Old Value", oldVal);
      console.log("New Value", newVal);
    },
  },
};
</script>

<style scoped>
.Main {
  padding: 50px;
  background-color: tomato;
}
</style>
