<template>
  <button v-on:click="showing = !showing">Show Conditionals</button>
  <div v-show="showing">
    <!-- //? ================= Conditional Rendering ================ -->
    <h2 v-if="num === 0">The number is 0</h2>
    <h2 v-else-if="num < 0">The number is negative</h2>
    <h2 v-else-if="num > 0">The number is positive</h2>
    <h2 v-else>The number is NOT 0</h2>
    <!-- display multiple elements conditionally. We can wrap in a div or template -->
    <template v-if="display">
      <h5>This</h5>
      <h5>is</h5>
      <h5>Text</h5>
    </template>
    <!-- v-show sets display:none and stays in the dom v-if removes from DOM -->
    <!-- //?================= List Rendering ================= -->
    <h2>List Rendering</h2>
    <ul>
      <li v-for="(name, index) in names" :key="name">
        {{ index }} - {{ name }}
      </li>
    </ul>
    <p>Fullnames</p>
    <ul>
      <li v-for="(name, key, index) in fullNames" :key="index">
        {{ name.first }} {{ name.last }}, key {{ key }}
      </li>
    </ul>
    <p>Fullnames if First name is Clark</p>
    <!-- You should not mix 'v-for' with 'v-if' -->
    <ul>
      <template v-for="(name, key, index) in fullNames" :key="index">
        <li v-if="name.first === 'Clark'">
          {{ name.first }} {{ name.last }}, key {{ key }}
        </li>
      </template>
    </ul>
  </div>
</template>
<script>
export default {
  name: "Conditionals",
  data() {
    return {
      num: -1,
      display: false,
      showing: false,
      names: ["Ella", "Anna", "Bella"],
      fullNames: [
        { first: "Bruce", last: "Wayne" },
        { first: "Clark", last: "Kent" },
        { first: "Princess", last: "Diana" },
      ],
    };
  },
};
</script>
<style lang=""></style>
