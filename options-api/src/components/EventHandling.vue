<template>
  <h2>{{ name }}</h2>
  <div>
    <!-- Event handelers can be defined in the methods object -->
    <!-- The event is implicitly passed in here -->
    <button v-on:click="changeName">Change Name</button>
    <button v-on:click="name = 'Richard'">Hide Name</button>
  </div>
  <h2>{{ count }}</h2>
  <div>
    <!-- To explicitly pass the event to a function with arguments we use $event -->
    <button v-on:click="increment(1, $event)">Increment 1</button>
    <button v-on:click="decrement(1)">Decrement 1</button>
    <!-- Shorthand syntax -->
    <button @click="increment(5)">Increment 5</button>
    <button @click="decrement(5)">Decrement 5</button>
  </div>
  <!-- Multiple event handlers now doesn't automatically add event to change name-->
  <button @click="changeName($event), increment(1, $event)">
    Increment 1
  </button>
</template>
<script>
export default {
  name: "EventHandling",
  data() {
    return {
      name: "Richard",
      count: 0,
    };
  },
  methods: {
    changeName(event) {
      this.name = "Ninja";
      console.log(event);
    },
    increment(amount, event) {
      this.count += amount;
      console.log(event);
    },
    decrement(amount) {
      this.count -= amount;
    },
  },
};
</script>
<style></style>
