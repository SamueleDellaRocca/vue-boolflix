<template>
  <div class="col-2 card mt-5 carta-film">
    <h1>{{ CartaFilmData.title }}</h1>
    <h2>{{ CartaFilmData.original_title }}</h2>
    <h3>{{ CartaFilmData.original_language }}</h3>
    <h4>{{ CartaFilmData.vote_average }}</h4>
  </div>
</template>

<script>
export default {
  name: "CartaFilm",

  props: {
    CartaFilmData: Object,
  },
};
</script>

<style lang="scss">
.carta-film {
  background-color: black;
  color: white;
}
</style>
