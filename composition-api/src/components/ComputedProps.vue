<template>
  <div class="main">
    <h1>Computed Properties</h1>
    <input type="text" placeholder="First Name" v-model="fname" />
    <input type="text" placeholder="Last Name" v-model="lname" />
    <h2>FullName: {{ fullName }}</h2>
    <h1>Composition - Refs</h1>
    <input type="text" placeholder="First Name" v-model="firstname" />
    <input type="text" placeholder="Last Name" v-model="lastname" />
    <h2>COMP Fullname: {{ fullname }}</h2>
    <h1>Composition - Reactive</h1>
    <input type="text" placeholder="First Name" v-model="reactiveFirstName" />
    <input type="text" placeholder="Last Name" v-model="reactiveLastName" />
    <h2>COMP Fullname: {{ ReactFullName }}</h2>
  </div>
</template>

<script>
import { computed, ref, reactive, toRefs } from "vue";

export default {
  name: "ComputedProps",
  setup() {
    const firstname = ref("");
    const lastname = ref("");

    const fullname = computed(() => {
      return `${firstname.value} ${lastname.value}`;
    });

    const state = reactive({
      reactiveFirstName: "",
      reactiveLastName: "",
    });

    const ReactFullName = computed(() => {
      return `${state.reactiveFirstName} ${state.reactiveLastName}`;
    });

    return {
      firstname,
      lastname,
      fullname,
      ReactFullName,
      ...toRefs(state),
    };
  },

  //   Options
  data() {
    return {
      fname: "",
      lname: "",
    };
  },
  computed: {
    fullName() {
      return `${this.fname} ${this.lname}`;
    },
  },
};
</script>

<style scoped>
.main {
  padding: 50px;
  background-color: thistle;
}
</style>
