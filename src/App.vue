<template>
  <div id="app">
    <header-boolflix @passaApi="funzioneApi" />
    <main-boolflix :array-data="arrayFilmProva" />
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
    };
  },

  methods: {
    funzioneApi(arrayFilmProva) {
      this.arrayFilmProva = arrayFilmProva;
    },
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap";
</style>
