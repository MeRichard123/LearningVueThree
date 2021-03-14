<template>
  <div>
    <h1>Volume Tracker (0-20)</h1>
    <h3>Current Volume - {{ volume }}</h3>
    <div>
      <!-- We need to watch the volume and warn the user if it's above 20 -->
      <button @click="volume += 2">Increase</button>
      <button @click="volume -= 2">Decrease</button>
    </div>
    <div>
      <input type="text" v-model="movie" />
      <input type="text" v-model="movieInfo.title" />
      <input type="text" v-model="movieInfo.actor" />
    </div>
  </div>
</template>
<script>
// Allow you to change data or computed props and execute some code in response to changes in value.
/*
use Computed Properties when:
- You need to compose new data from existing data
- You need to reduce the length if a variable
use watchers when:
- You need to check if a prop has reached a desired value and you are ready to preform an action
- You have to call an API in response to changes in the app data
- Apply transitions

*/
export default {
  name: "Watchers",
  data() {
    return {
      volume: 0,
      movie: "TMNT",
      movieInfo: {
        title: "",
        actor: "",
      },
    };
  },
  computed: {},
  watch: {
    //   Watchers watch a property and allow us to run code based on the changes on the prop
    volume(newValue, oldValue) {
      //   called each time the prop changes
      // Takes the new value as a parameter
      //   Called on change in the value
      if (newValue === 16 && newValue > oldValue) {
        alert(
          "Listening at a high volume for a prolonged time may damage your hearing"
        );
      }
    },
    movie: {
      handler(newVal) {
        console.log(`Calling API with movie name ${newVal}`);
      },
      //   immediate to true run this watcher on page load
      immediate: true,
    },
    movieInfo: {
      // By default watchers don't watch nested properties
      handler(newVal) {
        console.log(
          `Calling API with ${newVal.title} and actor ${newVal.actor} `
        );
      },
      //   This watches props and allow execution if the props of the movieInfo obj change
      deep: true,
    },
  },
};
</script>
<style lang=""></style>
