<template>
  <div id="app">
    <header-boolflix @passaApi="funzioneApi" @passaSerie="funzioneSerie" />
    <main-boolflix :array-data="arrayFilmProva" :array-serie="arraySerieTV" />
  </div>
</template>

<script>
import HeaderBoolflix from "./components/HeaderBoolflix.vue";
import MainBoolflix from "./components/MainBoolflix.vue";

export default {
  name: "App",
  components: {
    HeaderBoolflix,
    MainBoolflix,
  },

  data() {
    return {
      arrayFilmProva: null,
      arraySerieTV: null,
    };
  },

  methods: {
    funzioneApi(arrayFilmProva) {
      this.arrayFilmProva = arrayFilmProva;
    },

    funzioneSerie(arraySerieTV) {
      this.arraySerieTV = arraySerieTV;
    },
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap";
</style>
