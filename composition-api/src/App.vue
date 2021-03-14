<template>
  <div>
    <h1>Composition API</h1>
    <img alt="Vue logo" src="./assets/logo.png" />
    <Data />
    <DataReactive />
    <Reactivity />
    <ReactivityTwo />
    <Methods />
    <VModel />
    <ComputedProps />
    <Watchers />
    <ProvideInject />
    <LifecycleHooks />
    <TemplateRefs />
    <Person />
  </div>
</template>

<script>
import Data from "./components/Data";
import DataReactive from "./components/DataReactive";
import Reactivity from "./components/Reactivity";
import ReactivityTwo from "./components/ReactivityTwo";
import Methods from "./components/Methods";
import VModel from "./components/VModel";
import ComputedProps from "./components/ComputedProps";
import Watchers from "./components/Watchers";
import ProvideInject from "./components/ProvideInject/ProvideInject";
import LifecycleHooks from "./components/LifecycleHooks";
import TemplateRefs from "./components/TemplateRefs";
import Person from "./components/Props/Person";

export default {
  name: "App",
  components: {
    Data,
    DataReactive,
    Reactivity,
    ReactivityTwo,
    Methods,
    VModel,
    ComputedProps,
    Watchers,
    ProvideInject,
    LifecycleHooks,
    TemplateRefs,
    Person,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
button {
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  cursor: pointer;
  color: #555;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 4px;
}
button:disabled {
  background-color: hsl(0, 2%, 68%);
  cursor: not-allowed;
}
input[type="text"] {
  padding: 6px 12px;
  font-size: 14px;
  line-height: 1.42857143;
  color: #555;
  background-color: #fff;
  border: 1px solid #ccc;
  border-radius: 4px;
}
</style>
