<template>
  <button @click="showing = !showing">Toggle Computed Properties</button>
  <div v-show="showing">
    <h2>Fullname Computed- {{ fullname }}</h2>
    <button @click="changeFullname">Change Name</button>
    <button @click="items.push({ id: 4, title: 'keyboard', price: 50 })">
      Add Item
    </button>
    <!-- Computed are cached -->
    <p>Total - {{ orderTotal }}</p>
    <!-- methods are not -->
    <p>Method Total {{ getTotal() }}</p>
    <!-- The method prop will be recalculated when this input changes -->
    <!-- Cached -->
    <input type="text" v-model="country" />
    <template v-for="item in items" :key="item.id">
      <p v-if="item.price > 100">{{ item.title }} {{ item.price }}</p>
    </template>
    <h2 v-for="item in expensive" :key="item.id">
      {{ item.title }} - {{ item.price }}
    </h2>
  </div>
</template>
<script>
/*
Computed Properties are bound properties
For composing new data from existing source
cached calculations on update when dependencies change
useful for rendering the same data in multiple places
*/
export default {
  name: "computed properties",
  data() {
    return {
      name: "Bruce",
      lastName: "Wayne",
      items: [
        {
          id: 1,
          title: "Tv",
          price: 100,
        },
        {
          id: 2,
          title: "Phone",
          price: 200,
        },
        {
          id: 3,
          title: "Laptop",
          price: 300,
        },
      ],
      country: "",
      showing: false,
    };
  },
  methods: {
    getTotal() {
      console.log("Methods Property");
      return this.items.reduce((total, curr) => (total += curr.price), 0);
    },
    changeFullname() {
      this.fullname = "Clark Kent";
    },
  },
  computed: {
    //   Computed getters and setters. Setters let you change the value in the template
    fullname: {
      get() {
        return this.name + " " + this.lastName;
      },
      set(value) {
        const names = value.split(" ");
        this.name = names[0];
        this.lastName = names[1];
      },
    },
    // This is only a getter and is read-only
    orderTotal() {
      console.log("Computed Called");
      // Recalculated every time the items array changes
      return this.items.reduce((total, curr) => (total += curr.price), 0);
    },
    expensive() {
      return this.items.filter((item) => item.price > 100);
    },
  },
};
</script>
<style></style>
