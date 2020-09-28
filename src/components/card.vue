<template>
  <div class="row justify-content-center pt-5">
    <div class="card p-2 text-center">
      <div class="card-body p-1">
        <vue-load-image>
          <img slot="image" :src="gifs" alt="" class="img-fluid" />
          <div class="spinner-border" role="status" slot="preloader">
            <span class="sr-only">Loading...</span>
          </div>
          <div slot="error">error message</div>
        </vue-load-image>
      </div>
      <div @click="reloadGif()" class="btn btn-dark mt-2">Another Gif</div>
      <div @click="copyURL()" class="btn btn-dark mt-2">Copy Gif</div>
    </div>
  </div>
</template>

<script>
import axios from "axios"
import VueLoadImage from "vue-load-image"

export default {
  name: "Card",
  components: {
    "vue-load-image": VueLoadImage,
  },
  data() {
    return {
      gifs: "",
      giphyURL: process.env.VUE_APP_URL,
    }
  },

  async created() {
    try {
      const res = await axios.get(this.giphyURL)
      this.gifs = res.data.data.images.downsized_medium.url
    } catch (error) {
      this.gifs = "https://media.giphy.com/media/8L0Pky6C83SzkzU55a/giphy.gif"
    }
  },

  methods: {
    reloadGif() {
      axios.get(this.giphyURL).then((resp) => {
        this.gifs = resp.data.data.images.downsized_medium.url
      })
    },
    copyURL() {
      const el = document.createElement("textarea")
      el.value = this.gifs
      document.body.appendChild(el)
      el.select()
      document.execCommand("copy")
      document.body.removeChild(el)
    },
  },
}
</script>

<style scoped>
.card {
  width: 30rem;
  height: 25rem;
}

img {
  object-fit: scale-down;
  height: calc(20rem - 5rem);
}

.spinner-border {
  margin: 6rem 5%;
  width: 3rem;
  height: 3rem;
}
.btn:active {
  transform: scale(0.99);
  transition: 0.2s ease-in-out;
}
</style>
