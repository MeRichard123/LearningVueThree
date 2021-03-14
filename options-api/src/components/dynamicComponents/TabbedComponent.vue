<template>
  <div class="wrapper">
    <div>
      <button @click="activeTab = 'TabA'">Tab A</button>
      <button @click="activeTab = 'TabB'">Tab B</button>
      <button @click="activeTab = 'TabC'">Tab C</button>
    </div>
    <!-- Dynamic component uses the is attribute to tell vue what should be rendered -->
    <!-- Uses the component name -->
    <!-- Keep Alive component persists state between the components in the component tag -->
    <keep-alive>
      <component :is="activeTab" />
    </keep-alive>
    <!-- If use have a multi-step form keep alive stops state reset even if the dynamic component 
        is inactive. Keep alive can also prevent re-renders -->
    <!-- <TabA v-if="activeTab === 'TabA'" />
  <TabB v-if="activeTab === 'TabB'" />
  <TabC v-if="activeTab === 'TabC'" /> -->
  </div>
</template>

<script>
import TabA from "./TabA";
import TabB from "./TabB";
import TabC from "./TabC";

export default {
  name: "TabbedComponent",
  components: { TabA, TabB, TabC },
  data() {
    return {
      activeTab: "TabA",
    };
  },
};
</script>

<style scoped>
.wrapper {
  margin: 20px;
  background: tomato;
  padding: 50px;
  color: rgb(223, 223, 223);
}
</style>
