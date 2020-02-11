<template>
  <div id="app">
    <Card />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script>
import Card from "./components/card.vue";

// import HelloWorld from './components/HelloWorld.vue'

export default {
  name: "app",
  components: {
    Card
  }
};
</script>

<style>
@import "~bootstrap/dist/css/bootstrap.css";
</style>
