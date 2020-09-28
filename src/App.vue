<template>
  <div id="app" class="container-fluid align-items-center">
    <Card />
  </div>
</template>

<script>
import Card from "./components/card.vue";

export default {
  name: "app",
  components: {
    Card
  }
};
</script>

<style lang="scss">
@import "~bootstrap/dist/css/bootstrap.css";
#app{
  padding: 5% 10%;
}
body{
  background-color: #4c4c4c;

}
</style>
