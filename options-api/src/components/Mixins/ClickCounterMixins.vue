<template>
  <div>
    <button @click="incrementCount">Clicked {{ count }} times</button>
  </div>
</template>

<script>
/*
Mixins allow us to share component functionality
They are added to the mixins option 
- we can specify computed props, lifecycle hooks, data, watchers, methods
- The same option in the component and mixin will be merged and component options take priority
*/
import CounterMixin from "./CounterMixin";

export default {
  name: "ClickCounterMixins",
  mixins: [CounterMixin],
  data() {
    return {
      count: 100,
    };
  },
};
</script>

<style scoped></style>
