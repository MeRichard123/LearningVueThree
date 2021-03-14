<template>
  <div class="main">
    <input type="text" ref="inputRef" />
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
export default {
  name: "TemplateRefs",
  setup() {
    const inputRef = ref(null);
    onMounted(() => {
      inputRef.value.focus();
    });

    return {
      inputRef,
    };
  },
  mounted() {
    this.$refs.inputRef.focus();
  },
};
</script>

<style scoped>
.main {
  padding: 50px;
  background-color: hsl(328, 59%, 61%);
}
</style>
