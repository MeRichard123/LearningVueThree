<template>
  <div>
    <h5>{{ reactiveGreet }}</h5>
  </div>
</template>

<script>
import { reactive } from "vue";

export default {
  name: "Data",
  setup() {
    //   Reactive lets use avoid having to use .value
    // Use Ref for primitive types as Reactive can only manage objects
    // use Reactive when you hae lots of related primitive types
    // Return a reactive reference
    const person = reactive({
      firstName: "Princess",
      lastName: "Diana",
      heroName: "Wonder Woman",
    });
    const reactiveGreet = `Hello ${person.firstName} ${person.lastName} a.k.a ${person.heroName}`;

    return {
      reactiveGreet,
    };
  },
};
</script>

<style scoped></style>
