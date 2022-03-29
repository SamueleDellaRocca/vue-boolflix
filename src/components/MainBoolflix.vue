<template>
  <main>
    <div class="row gap-5 text-center justify-content-center pb-5">
      <card-film
        v-for="cartaFilm in ArrayData"
        :key="cartaFilm.id"
        :carta-film-data="cartaFilm"
      />
    </div>
  </main>
</template>

<script>
import CardFilm from "./CardFilm.vue";

export default {
  components: { CardFilm },
  name: "MainBoolflix",

  data() {
    return {};
  },

  props: {
    ArrayData: Array,
  },
};
</script>

<style>
main {
  min-height: calc(100vh - 100px);
  background-color: darkgray;
}

.row {
  --bs-gutter-x: 0rem !important;
}
</style>
