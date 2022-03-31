<template>
  <div class="col-6 card mt-5 carta-film position-relative p-1">
    <img
      v-if="CartaFilmData.poster_path != null"
      :src="`https://image.tmdb.org/t/p/w342${CartaFilmData.poster_path}`"
      :alt="CartaFilmData.original_title"
    />
    <div class="assoluto">
      <h4>{{ CartaFilmData.title }}</h4>
      <div>{{ CartaFilmData.original_title }}</div>
      <div>
        <lang-flag :iso="CartaFilmData.original_language" :squared="false" />
      </div>
      <div>{{ CartaFilmData.vote_average }}</div>
      <span v-for="(element, index) in funzioneStelle()" :key="'stella' + index"
        >&#11088;</span
      >
      <br />
      <div v-for="attore in arrayAttori" :key="attore.cast_id">
        {{ attore.name }}
      </div>
    </div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
import axios from "axios";

export default {
  name: "CartaFilm",

  data() {
    return {
      arrayAttori: null,
    };
  },

  methods: {
    funzioneStelle() {
      let ArrayStelle = [];
      for (
        let index = 0;
        index < Math.floor(this.CartaFilmData.vote_average) / 2;
        index++
      ) {
        ArrayStelle.push(index);
      }
      return ArrayStelle;
    },
  },

  created() {
    axios
      .get(
        `https://api.themoviedb.org/3/movie/${this.CartaFilmData.id}/credits?api_key=5bbb62e6d70ca4e59aa9a9931e821fce&language=en-US`
      )
      .then((response) => {
        this.arrayAttori = response.data.cast;
      })
      .then(() => {
        this.arrayAttori.splice(5, this.arrayAttori.length - 5);
      });
  },

  props: {
    CartaFilmData: Object,
  },

  components: {
    LangFlag,
  },
};
</script>

<style lang="scss" scoped>
.carta-film {
  background-color: black;
  color: white;
  width: 260px;
  height: 380px;
}

img {
  width: 100%;
  height: 100%;
  z-index: 3;
}

.carta-film:hover img {
  transition: 1s;
  opacity: 0;
}

.assoluto {
  width: 95%;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  div {
    font-size: 1.2rem;
  }
}
</style>
