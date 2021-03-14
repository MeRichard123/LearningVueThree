<template>
  <!-- When passing non prop attributes we can choose where it will be applied -->
  <div class="article">
    <!-- If we wanted the Component NonPropAttributes to be on this h2 we v-bind the $attrs -->
    <!-- However they will still be present on the parent node -->
    <h1 v-bind="$attrs">Article Component</h1>
    <h2>{{ title }} - {{ likes }} Likes</h2>
    <p>Published - {{ isPublished ? "Yes" : "No" }}</p>
  </div>
</template>

<script>
export default {
  name: "PropTypesArticle",
  props: {
    //   Settings a prop to required gives you a warning in console if it is missing
    title: {
      type: String,
      required: true,
      default: "Default Title",
    },
    likes: Number,
    isPublished: Boolean,
  },
  //   Inherit Attributes stops the root node from inheriting attributes from the component
  inheritAttrs: false,
};
</script>

<style scoped>
.article {
  padding: 20px 40px;
  border: 2px solid hsl(0, 0%, 17%);
  border-radius: 5px;
  color: hsl(0, 0%, 17%);
  margin: auto;
  max-width: 50vw;
}
</style>
