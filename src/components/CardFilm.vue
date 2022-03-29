<template>
  <div class="col-3 card mt-5">
    <h1>{{ CartaFilmData.title }}</h1>
    <h2>{{ CartaFilmData.original_title }}</h2>
    <h3>{{ CartaFilmData.release_date }}</h3>
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

<style></style>
