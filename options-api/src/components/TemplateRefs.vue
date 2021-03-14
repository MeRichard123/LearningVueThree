<template>
  <div>
    <input type="text" ref="inputRef" />
    <PostList ref="postListRef" />
  </div>
</template>

<script>
import PostList from "./NetworkRequests/PostList";
export default {
  name: "TemplateRefs",
  components: {
    PostList,
  },
  mounted() {
    //   To use a ref we access the $refs property
    this.$refs.inputRef.focus();
    console.log(this.$refs.postListRef);
  },
};
</script>

<style scoped></style>
