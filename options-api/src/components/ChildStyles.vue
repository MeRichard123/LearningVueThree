<template>
  <div>
    <h4>Non Slot in Child</h4>
    <slot></slot>
  </div>
</template>

<script>
export default {
  name: "ChildStyles",
};
</script>

<style scoped>
/*
1. By Default, a component styles are applied globally in the component tree 
2. The Scoped attribute ensure a component's CSS will only apply to its own HTML*

with scoped, the parent component styles will not leak into child components: 
However, a child component's root node will be affected by both the parent's 
scoped CSS and the child's scoped CSS. This is by design so that the parent can
style the child root element for layout purposes: 

This can be avoided using css modules

3. Slot content will inherit the styles of the component the content is defined in
*/
h4 {
  color: orange;
}
</style>
