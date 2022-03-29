<template>
  <div class="col-2 card mt-5 carta-serie">
    <h1>{{ CartaSerieData.name }}</h1>
    <h2>{{ CartaSerieData.original_name }}</h2>
    <h3>
      <lang-flag :iso="CartaSerieData.original_language" :squared="false" />
    </h3>
    <h4>{{ CartaSerieData.vote_average }}</h4>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";

export default {
  name: "CartaSerie",

  props: {
    CartaSerieData: Object,
  },

  components: {
    LangFlag,
  },
};
</script>

<style lang="scss" scoped>
.carta-serie {
  background-color: black;
  color: white;
}
</style>
