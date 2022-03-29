<template>
  <div id="app">
    <header-boolflix @ricerca="funzioneRicerca" />
    <main-boolflix :film-ricercato="filmRicercato" />
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
      filmRicercato: "",
    };
  },

  methods: {
    funzioneRicerca(filmRicercato) {
      this.filmRicercato = filmRicercato;
    },
  },
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap";
</style>
