<template>
  <div>
    <h1>Learning VueJS!</h1>
    <img alt="Vue logo" src="./assets/logo.png" />
    <!-- Mustache syntax: Text interpolation -->
    <div>Name from the data function: {{ greet }} {{ name }}</div>
    <!-- Using a directive to bind text: This will replace the whole contents if the div  -->
    <div v-text="social"></div>
    <Binding />
    <Methods />
    <Conditionals />
    <EventHandling />
    <FormHandling />
    <!-- the v-once will one render once and not re-render after changes -->
    <!-- Optimises update performance -->
    <h2 v-once>{{ name }}</h2>
    <!-- v-pre skips compilation for the element like the html pre tag-->
    <!-- Stops Vue from doing things with = faster compilation -->
    <h2 v-pre>{{ name }}</h2>
    <ComputedProperties />
    <Watchers />
    <!-- kebab case is the naming convention for props -->
    <!-- Vue will auto convert to camel case in javascript so you can access it in the component -->
    <PropComponent name="Ella" person-age="16" />
    <PropComponent name="Daniel" person-age="16" />
    <PropComponent name="Sandwich" person-age="17" />
    <!-- Dynamic Props with v-bind -->
    <PropComponent :name="name" person-age="17" />
    <!-- We use V-Bind to ensure Vue treats the likes prop as a number -->
    <!-- Non Prop Attributes are ones such as class, id -->
    <PropTypesArticle
      title="Article One"
      :likes="50"
      :isPublished="true"
      id="Article"
    />
    <ProvideInject />
    <!-- Provide doesn't let you inject -->
    <!-- To get around this we add a data property and set it as the provider-->
    <!-- this requires us to change provide from a value to a function -->
    <p>username: {{ name }}</p>
    <button @click="showPopUp = true">Show Pop Up</button>
    <!-- Listen to custom close event -->
    <CustomEvents v-show="showPopUp" @close="closePopup" />
    <!-- V-model on custom components -->
    <Input v-model="name" />

    <Slots>
      <h1>This is Custom Content</h1>
      <p>On a custom component</p>
    </Slots>
    <Slots></Slots>
    <Slots>
      <template v-slot:header>
        <h3>Card Header</h3>
      </template>
      <template v-slot:default>
        <img src="https://picsum.photos/200" alt="" />
      </template>
      <template v-slot:footer>
        <p>Made by me</p>
      </template>
    </Slots>
    <!-- Slot Props -->
    <NameList>
      <!-- We define a slit and create a prop to store the data props -->
      <template v-slot:default="slotProps">
        {{ slotProps.firstName }} {{ slotProps.lastName }}
      </template>
    </NameList>
    <NameList>
      <!-- We define a slot and create a prop to store the data props -->
      <template v-slot:default="slotProps">
        {{ slotProps.firstName }}
      </template>
    </NameList>
    <h4>Parent Styles</h4>
    <ChildStyles>
      <h4>Child Styles in Slot coming from parent</h4>
    </ChildStyles>
    <TabbedComponent />
    <!-- The teleport component will move the TeleportComponent to the div with the ID of portal-root -->
    <teleport to="#portal-root">
      <TeleportComponent />
    </teleport>
    <CreatePost />
    <PostList />
    <LifeCycleHooks />
    <TemplateRefs />
    <ClickCounterMixins />
    <HoverCounter />
  </div>
</template>

<script>
import Binding from "./components/Binding";
import Methods from "./components/Methods";
import Conditionals from "./components/Conditionals";
import EventHandling from "./components/EventHandling";
import FormHandling from "./components/FormHandling";
import ComputedProperties from "./components/ComputedProperties";
import Watchers from "./components/Watchers";
import PropComponent from "./components/PropComponent";
import PropTypesArticle from "./components/PropTypesArticle";
import ProvideInject from "./components/ProvideInject";
import CustomEvents from "./components/CustomEvents";
import Input from "./components/Input";
import Slots from "./components/Slots";
import NameList from "./components/NameList";
import ChildStyles from "./components/ChildStyles";
import TabbedComponent from "./components/dynamicComponents/TabbedComponent";
import TeleportComponent from "./components/TeleportComponent";
import PostList from "./components/NetworkRequests/PostList";
import CreatePost from "./components/NetworkRequests/CreatePost";
import LifeCycleHooks from "./components/LifecycleHooks/LifeCycleHooks";
import TemplateRefs from "./components/TemplateRefs";
import ClickCounterMixins from "./components/Mixins/ClickCounterMixins";
import HoverCounter from "./components/Mixins/HoverCounter";

export default {
  name: "App",
  components: {
    Binding,
    Methods,
    Conditionals,
    EventHandling,
    FormHandling,
    ComputedProperties,
    Watchers,
    PropComponent,
    PropTypesArticle,
    ProvideInject,
    CustomEvents,
    Input,
    Slots,
    NameList,
    ChildStyles,
    TabbedComponent,
    TeleportComponent,
    PostList,
    CreatePost,
    LifeCycleHooks,
    TemplateRefs,
    ClickCounterMixins,
    HoverCounter,
  },
  // We can export data in an object this is passed to the template
  // we bind this in the template
  data() {
    return {
      name: "Richard",
      greet: "Hello",
      social: "RichardMe123",
      script: "<b>This is bold HTML with v-html<b>",
      showPopUp: false,
    };
  },
  provide() {
    // Define props we want the child components to consume
    // See src/components/nestedComponents/NestedB to see inject
    /*
    If the prop is used only further down you can specify the provide object.
    If the data has to be used in the same component as well as down the tree
    specify provide as a function which returns an object.
    The object can then use data and computed properties defined in the providing component
    which can be consumed in the receiving component using the inject option
    */
    return {
      username: this.name,
    };
  },
  methods: {
    closePopup(name) {
      this.showPopUp = false;
      console.log(name);
    },
  },
};
</script>

<style>
/* By default all component styles are applied globally */
/* See ChildStyles.vue */
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
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
/* Global Styles */
h4 {
  color: lawngreen;
}
</style>
