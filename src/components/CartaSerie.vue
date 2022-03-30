<template>
  <div class="col-2 card mt-5 carta-serie position-relative p-1">
    <img
      v-show="CartaSerieData.poster_path != null"
      :src="`https://image.tmdb.org/t/p/w342${CartaSerieData.poster_path}`"
      :alt="CartaSerieData.original_title"
    />
    <div class="assoluto">
      <h4>{{ CartaSerieData.name }}</h4>
      <div>{{ CartaSerieData.original_name }}</div>
      <div>
        <lang-flag :iso="CartaSerieData.original_language" :squared="false" />
      </div>
      <div>{{ CartaSerieData.vote_average }}</div>
      <span v-for="(element, index) in funzioneStelle()" :key="index"
        >&#11088;</span
      >
      <div v-for="attore in funzioneChiamataAttori" :key="attore.id">
        {{ attore.name }}
      </div>
    </div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
import axios from "axios";

export default {
  name: "CartaSerie",

  data() {
    return {
      arrayAttori: null,
    };
  },

  methods: {
    funzioneStelle() {
      let ArrayStelle = [];
      for (
        let index = 0;
        index < Math.floor(this.CartaSerieData.vote_average) / 2;
        index++
      ) {
        ArrayStelle.push(index);
      }
      return ArrayStelle;
    },

    funzioneChiamataAttori() {
      axios
        .get(
          `https://api.themoviedb.org/3/tv/${this.CartaSerieData.id}/credits?api_key=5bbb62e6d70ca4e59aa9a9931e821fce&language=en-US`
        )
        .then((response) => {
          this.arrayAttori = response.data.cast;
          console.log(response);
        });
      this.arrayAttori.length = 5;
      console.log(this.arrayAttori);
      return this.arrayAttori;
    },
  },

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
  transition: 1s;
  opacity: 0;
}

.assoluto {
  width: 95%;
  position: absolute;
  left: 50%;
  top: 50%;
  transform: translate(-50%, -50%);
  div {
    font-size: 1.2rem;
  }
}
</style>
