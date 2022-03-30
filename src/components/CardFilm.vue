<template>
  <div class="col-2 card mt-5 carta-film position-relative p-1">
    <img
      v-show="CartaFilmData.poster_path != null"
      :src="`https://image.tmdb.org/t/p/w342${CartaFilmData.poster_path}`"
      :alt="CartaFilmData.original_title"
    />
    <div class="assoluto">
      <h3>{{ CartaFilmData.title }}</h3>
      <div>{{ CartaFilmData.original_title }}</div>
      <div>
        <lang-flag :iso="CartaFilmData.original_language" :squared="false" />
      </div>
      <div>{{ CartaFilmData.vote_average }}</div>
    </div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";

export default {
  name: "CartaFilm",

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
  width: 100%;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  div {
    font-size: 1.2rem;
  }
}
</style>
