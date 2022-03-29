<template>
  <div class="col-2 card mt-5 carta-serie">
    <h1>{{ CartaSerieData.name }}</h1>
    <h2>{{ CartaSerieData.original_name }}</h2>
    <h3>{{ CartaSerieData.original_language }}</h3>
    <h4>{{ CartaSerieData.vote_average }}</h4>
  </div>
</template>

<script>
export default {
  name: "CartaSerie",

  props: {
    CartaSerieData: Object,
  },
};
</script>

<style lang="scss" scoped>
.carta-serie {
  background-color: black;
  color: white;
}
</style>
