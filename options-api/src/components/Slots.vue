<template>
  <div class="card">
    <!-- Adding content in the custom component tags will replace the slot -->
    <!-- If none is added the default is displayed -->
    <!-- <slot>
      <h2>204</h2>
      <p>No content</p>
    </slot> -->
    <!-- Named Slots -->

    <div id="card-header">
      <slot name="header"> </slot>
    </div>
    <div id="card-content">
      <!-- Unnamed is the default slot -->
      <slot>
        <h2>204</h2>
        <p>No content</p>
      </slot>
    </div>
    <div id="card-footer">
      <slot name="footer"></slot>
    </div>
  </div>
</template>

<script>
/*
    Props allow you to re-use components by passing in different data
    Great for Reusability but has a strict parent-child relationship
    The child is in control of HTML and the parent can only pass in data
    Slots are more powerful
    allow parent component to control the content in a child by embedding it
    */
export default {
  name: "Slots",
};
</script>

<style scoped>
.card {
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2);
  transition: 0.3s;
  padding: 16px;
  margin: 20px 0;
  width: 200px;
}
.card:hover {
  box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2);
}
</style>
