<template>
  <div class="col-6 card mt-5 carta-film position-relative p-1">
    <img
      v-if="CartaFilmData.poster_path != null"
      :src="`https://image.tmdb.org/t/p/w342${CartaFilmData.poster_path}`"
      :alt="CartaFilmData.original_title"
    />
    <img
      v-else
      src="https://thumbs.dreamstime.com/b/movie-film-company-logo-design-vector-template-movie-film-company-logo-design-inspiration-vector-template-167661473.jpg"
      alt="logo-film"
    />
    <div class="assoluto">
      <h5>{{ CartaFilmData.title }}</h5>
      <div>{{ CartaFilmData.original_title }}</div>
      <div>
        <lang-flag :iso="CartaFilmData.original_language" :squared="false" />
      </div>
      <div>{{ CartaFilmData.vote_average }}</div>
      <span v-for="(element, index) in funzioneStelle()" :key="'stella' + index"
        >&#11088;</span
      >
      <br />
      <div v-for="attore in arrayAttori" :key="attore.cast_id">
        {{ attore.name }}
      </div>
      <div v-if="CartaFilmData.overview !== ''">
        <button @click="funzioneVisible" class="btn_trama">TRAMA</button>
      </div>
      <div v-if="visibilita" class="trama">
        {{ CartaFilmData.overview }}
      </div>
    </div>
  </div>
</template>

<script>
import LangFlag from "vue-lang-code-flags";
import axios from "axios";

export default {
  name: "CartaFilm",

  data() {
    return {
      arrayAttori: null,
      visibilita: false,
    };
  },

  methods: {
    funzioneStelle() {
      let ArrayStelle = [];
      for (
        let index = 0;
        index < Math.floor(this.CartaFilmData.vote_average) / 2;
        index++
      ) {
        ArrayStelle.push(index);
      }
      return ArrayStelle;
    },

    funzioneVisible() {
      if (this.visibilita == false) {
        this.visibilita = true;
      } else {
        this.visibilita = false;
      }
    },
  },

  created() {
    axios
      .get(
        `https://api.themoviedb.org/3/movie/${this.CartaFilmData.id}/credits?api_key=5bbb62e6d70ca4e59aa9a9931e821fce&language=en-US`
      )
      .then((response) => {
        this.arrayAttori = response.data.cast;
      })
      .then(() => {
        this.arrayAttori.splice(5, this.arrayAttori.length - 5);
      });
  },

  props: {
    CartaFilmData: Object,
  },

  components: {
    LangFlag,
  },
};
</script>

<style lang="scss" scoped>
.carta-film {
  background-color: black;
  color: white;
  width: 260px;
  height: 380px;
}

img {
  width: 100%;
  height: 100%;
}

.carta-film:hover img {
  display: none;
}

.carta-film:hover .assoluto {
  display: block;
}

.assoluto {
  position: absolute;
  width: 100%;
  top: 10px;
  left: 0px;
  display: none;
  z-index: 100;
}

.btn_trama {
  margin-top: 15px;
  background-color: red;
  border: 1px solid black;
  padding: 5px 15px;
  font-weight: bold;
  position: relative;
}

.trama {
  background-color: black;
  color: white;
  padding: 25px;
  width: 100%;
  max-height: 200px;
  overflow: auto;
}
</style>
