<template>
  <div class="col-2 card mt-5 carta-film">
    <h1>{{ CartaFilmData.title }}</h1>
    <h2>{{ CartaFilmData.original_title }}</h2>
    <h3>
      <lang-flag :iso="CartaFilmData.original_language" :squared="false" />
    </h3>
    <h4>{{ CartaFilmData.vote_average }}</h4>
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
</style>
