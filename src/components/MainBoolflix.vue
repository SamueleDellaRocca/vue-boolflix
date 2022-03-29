<template>
  <main>
    <button @click="funzioneApi">fai partire chiamata al server</button>
    <div class="row gap-5 text-center justify-content-center">
      <card-film
        v-for="cartaFilm in arrayFilmProva"
        :key="cartaFilm.id"
        :carta-film-data="cartaFilm"
      />
    </div>
  </main>
</template>

<script>
import CardFilm from "./CardFilm.vue";
import axios from "axios";

export default {
  components: { CardFilm },
  name: "MainBoolflix",

  data() {
    return {
      arrayFilmProva: null,
    };
  },

  props: {
    FilmRicercato: String,
  },

  methods: {
    funzioneApi() {
      axios
        .get(
          `https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=${this.FilmRicercato}`
        )
        .then((response) => {
          console.log(response);
          this.arrayFilmProva = response.data.results;
        });
    },
  },
};
</script>

<style>
main {
  min-height: calc(100vh - 100px);
  background-color: darkgray;
}

.row {
  --bs-gutter-x: 0rem !important;
}
</style>
