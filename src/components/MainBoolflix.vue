<template>
  <main>
    <h1 v-if="ArrayData == null || ArrayData.length == 0" class="intro">
      Cerca Qualcosa
    </h1>
    <div v-else>
      <h1 class="text-center pt-5 rosso">MOVIES</h1>
      <div class="row gap-5 text-center justify-content-center pb-5">
        <card-film
          v-for="cartaFilm in ArrayData"
          :key="cartaFilm.id"
          :carta-film-data="cartaFilm"
        />
      </div>

      <h1 class="text-center pt-5 rosso">SERIES</h1>
      <div class="row gap-5 text-center justify-content-center pb-5">
        <carta-serie
          v-for="cartaSerie in ArraySerie"
          :key="cartaSerie.id"
          :carta-serie-data="cartaSerie"
        />
      </div>
    </div>
  </main>
</template>

<script>
import CardFilm from "./CardFilm.vue";
import CartaSerie from "./CartaSerie.vue";

export default {
  components: {
    CardFilm,
    CartaSerie,
  },
  name: "MainBoolflix",

  data() {
    return {};
  },

  props: {
    ArrayData: Array,
    ArraySerie: Array,
  },
};
</script>

<style lang="scss" scoped>
main {
  min-height: calc(100vh - 100px);
  background-color: darkgray;
  position: relative;
}

.row {
  --bs-gutter-x: 0rem !important;
}

.rosso {
  color: black;
  font-size: 4rem;
}

.intro {
  font-size: 4rem;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
