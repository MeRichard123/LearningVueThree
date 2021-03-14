<template>
  <!-- Teleport allows you define a component in one place and then move it elsewhere -->
  <!-- Like a react Portal -->
  <!-- 1. Add non root dom node in index.html -->
  <!-- 2. wrap the component in the <teleport></teleport> tag where ever the component is placed -->
  <!-- Here we have added it to the app component -->
  <div>
    <h2>Portal Component</h2>
  </div>
</template>

<script>
export default {
  name: "TeleportComponent",
};
</script>

<style scoped></style>
