<template>
  <button v-on:click="showElement = !showElement">
    {{ !showElement ? "show" : "hide" }} Binding
  </button>
  <div v-show="showElement">
    <!--//? ================= Attribute binding ================= -->
    <h2 v-bind:id="headingId">Heading with dynamic attribute</h2>
    <button v-bind:disabled="isDisabled">Bind</button>
    <!-- Class name binding -->
    <h3 class="underline" v-bind:class="status">
      This has a dynamic class name
    </h3>
    <!-- Conditional classes promoted class if isPromoted is true-->
    <h2 v-bind:class="isPromoted && 'promoted'">Promoted?</h2>
    <p v-bind:class="isSoldOut ? 'sold' : 'new'">Movie Sold out? Ternary</p>
    <p v-bind:class="['promoted', 'new']">Newly Promoted Movie</p>
    <!-- Array class binding -->
    <p v-bind:class="[isPromoted && 'promoted', isSoldOut ? 'sold' : 'new']">
      Array conditional
    </p>
    <!-- Object class Binding -->
    <!-- key = className and value is the condition -->
    <p
      v-bind:class="{
        promoted: isPromoted,
        new: !isSoldOut,
        sold: isSoldOut,
      }"
    >
      Object Conditional
    </p>
    <!-- Binding Styles -->
    <p
      v-bind:style="{
        color: highlightColour,
        'font-size': headerSize + 'px',
      }"
    >
      Style Binding
    </p>
    <!-- Bind styles with objects -->
    <!-- This can also be an array of objects -->
    <p v-bind:style="headerStyles">Style with Object</p>
    <!-- Shorthand for v-bind -->
    <h2 :class="isPromoted && 'promoted'">Promoted?</h2>
    <p :class="isSoldOut ? 'sold' : 'new'">Movie Sold out? Ternary</p>
    <p :class="['promoted', 'new']">Newly Promoted Movie</p>
  </div>
</template>
<script>
export default {
  name: "Binding",
  data() {
    return {
      headingId: "heading",
      isDisabled: true,
      status: "danger",
      isPromoted: true,
      isSoldOut: true,
      highlightColour: "orange",
      headerSize: 50,
      showElement: false,
      headerStyles: {
        color: "orange",
        fontSize: "50px",
        padding: "20px",
      },
    };
  },
};
</script>
<style>
#heading {
  color: burlywood;
}
.underline {
  text-decoration: underline;
}
.danger {
  color: red;
}
.promoted {
  font-style: italic;
}
.new {
  font-weight: bold;
}
.sold {
  text-decoration: line-through;
}
</style>
