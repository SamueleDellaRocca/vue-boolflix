<template>
  <div
    class="d-flex col-12 justify-content-between altezza align-items-center pad"
  >
    <h1 class="text-red">Boolflix</h1>
    <div>
      <input
        @keyup.enter="funzioneApi()"
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
      arraySerieTV: null,
    };
  },

  methods: {
    funzioneApi() {
      if (this.filmRicercato.trim() == "") {
        this.arrayFilmProva = [];
        this.$emit("passaApi", this.arrayFilmProva);
      } else {
        axios
          .get(
            `https://api.themoviedb.org/3/search/movie?api_key=5bbb62e6d70ca4e59aa9a9931e821fce&query=${this.filmRicercato}`
          )
          .then((response) => {
            this.arrayFilmProva = response.data.results;
            this.$emit("passaApi", this.arrayFilmProva);
            console.log(response);
          })

          .then(() =>
            axios.get(
              `https://api.themoviedb.org/3/search/tv?api_key=5bbb62e6d70ca4e59aa9a9931e821fce&language=it_IT&query=${this.filmRicercato}`
            )
          )
          .then((responseSerieTv) => {
            console.log(responseSerieTv);
            this.arraySerieTV = responseSerieTv.data.results;
            this.$emit("passaSerie", this.arraySerieTV);
            console.log(this.arrayFilmProva);
            console.log(this.arraySerieTV);
          });
      }
    },
  },
};
</script>

<style lang="scss" scoped>
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
