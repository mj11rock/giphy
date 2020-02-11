<template>
  <div class="container">
    <div class="row">
      <!-- <div class="col-4 bg-danger m-2" v-for="todo of todos" :key="todo.id">{{todo.id}}</div> -->
      <img :src="gifs.images.downsized_large.url" alt />
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "Card",
  data() {
    return {
      todos: [],
      gifs: [],
      giphyURL:
        "https://api.giphy.com/v1/gifs/random?api_key=CbSHaXroSuxGYrTZ95AdA5XHGptvSb6u&tag=doughnut&rating=pg-13"
    };
  },

  async created() {
    // Giphy API URL
    const res = await axios.get(this.giphyURL);

    this.gifs = res.data.data;
  },
  methods: {
    newGif() {
      axios.get(this.giphyURL).then(resp => {
        this.gifs = resp.data;
      });
    },
    renderGif() {}
  }
};
</script>

<style scoped></style>
