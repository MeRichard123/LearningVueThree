<template>
  <div>
    <h1>Parent</h1>
    <button @click="showChild = !showChild">Toggle Child</button>
    <Child v-if="showChild" />
  </div>
</template>

<script>
/*
1. Creating 
2. Mounting
3. Updating
4. Unmounting

There are 13 lifecycle hooks which we can use to hook
into these phases in the lifecycle of a component and execute some code

Creation - a component is being created
---------
METHODS - 
    beforeCreate() - no watchers are processed, 
    created() - API Calls

Mounting - HTML is rendered
--------
METHODS -
    beforeMount() 
    mounted() -if we need to modify DOM immediately before or after render

Updating - A Reactive prop such as a computed is changes
-------
    beforeUpdate()
    updated() - called after the dom has been changed

Unmounting -
-------
    beforeUnmount() - clean up
    unmounted() 

Misc
------
    activated() - keep alive component in dynamic components, Called when a keep alive component is activated
    deactivated() - Called when keep alive is no longer active
    errorCaptured() - Called when an error from any descending component is captured
    renderTracked() - Useful for debugging show what caused a render
    renderTriggered() - 
*/
import Child from "./Child";

export default {
  name: "LifeCycleHooks",
  components: {
    Child,
  },
  data() {
    return {
      showChild: true,
    };
  },
  beforeCreate() {
    console.log("Parent beforeCreate()");
  },
  created() {
    console.log("Parent created()");
  },
  beforeMount() {
    console.log("Parent beforeMount()");
  },
  mounted() {
    console.log("Parent Mounted()");
  },
  beforeUpdate() {
    console.log("Parent beforeUpdate()");
  },
  updated() {
    console.log("Parent unmounted()");
  },
  beforeUnmount() {
    console.log("Parent beforeUnmount()");
  },
  unmounted() {
    console.log("Parent unmounted()");
  },
};
</script>

<style scoped></style>
