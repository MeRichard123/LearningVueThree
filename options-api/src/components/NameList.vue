<template>
  <!-- We can add props to the slot which will be sent to the parent -->
  <!-- V-Bind will pass data to the parent component from a slot -->
  <!-- That way you can structure the template however you want -->
  <p v-for="name in names" :key="name.firstname">
    <slot :firstName="name.firstname" :lastName="name.lastName"></slot>
  </p>
</template>

<script>
export default {
  name: "NameList",
  data() {
    return {
      names: [
        { firstname: "Bruce", lastName: "Wayne" },
        { firstname: "Clark", lastName: "Kent" },
        { firstname: "Princess", lastName: "Diana" },
      ],
    };
  },
};
</script>

<style scoped></style>
