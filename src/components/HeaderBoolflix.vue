<template>
  <div
    class="d-flex col-12 justify-content-between altezza align-items-center pad"
  >
    <h1 class="text-red">Boolflix</h1>
    <div>
      <input
        @keyup.enter="funzioneApi(), $emit('passaApi', arrayFilmProva)"
        v-model="filmRicercato"
        type="text"
        placeholder="Cerca il tuo film preferito"
        class="m-1 padd1"
      />
      <button @click="funzioneApi()" class="padd rosso">Cerca</button>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "HeaderBoolflix",

  data() {
    return {
      filmRicercato: "",
      arrayFilmProva: null,
    };
  },

  methods: {
    funzioneApi() {
      if (this.filmRicercato.trim() == "") {
        this.arrayFilmProva = [];
      } else {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie?api_key=e99307154c6dfb0b4750f6603256716d&query=${this.filmRicercato}`,
            console.log(this.FilmRicercato)
          )
          .then((response) => {
            console.log(response);
            this.arrayFilmProva = response.data.results;
            this.$emit("passaApi", this.arrayFilmProva);
            this.filmRicercato = "";
          });
      }
    },
  },
};
</script>

<style>
.row {
  --bs-gutter-x: 0rem;
}

.altezza {
  height: 100px;
  background-color: black;
}

.pad {
  padding: 0 4rem;
}

.text-red {
  color: red;
  text-transform: uppercase;
}

.padd1 {
  padding: 5px;
  width: 300px;
}

.padd {
  padding: 5px 20px;
}

.rosso {
  background-color: red;
  text-transform: uppercase;
}
</style>
