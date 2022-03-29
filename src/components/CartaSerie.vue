<template>
  <div class="col-2 card mt-5 carta-serie position-relative p-1">
    <img
      v-show="CartaSerieData.poster_path != null"
      :src="`https://image.tmdb.org/t/p/w342${CartaSerieData.poster_path}`"
      :alt="CartaSerieData.original_title"
    />
    <div class="assoluto">
      <h3>{{ CartaSerieData.name }}</h3>
      <div>{{ CartaSerieData.original_name }}</div>
      <div>
        <lang-flag :iso="CartaSerieData.original_language" :squared="false" />
      </div>
      <div>{{ CartaSerieData.vote_average }}</div>
    </div>
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

img {
  width: 100%;
  height: 100%;
  z-index: 3;
}

.carta-serie:hover img {
  z-index: -1;
}

.assoluto {
  width: 100%;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  div {
    font-size: 1.3rem;
  }
}
</style>
