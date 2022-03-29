<template>
  <div
    class="d-flex col-12 justify-content-between altezza align-items-center padding"
  >
    <h1 class="text-red">Boolflix</h1>
    <div>
      <input
        @keyup.enter="$emit('ricerca', filmRicerato)"
        v-model="filmRicerato"
        type="text"
        placeholder="Cerca il tuo film preferito"
        class="m-1 padd1"
      />
      <button @click="$emit('ricerca', filmRicerato)" class="padd rosso">
        Cerca
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HeaderBoolflix",

  data() {
    return {
      filmRicerato: "",
    };
  },
};
</script>

<style>
.row {
  --bs-gutter-x: 0rem;
}

.altezza {
  height: 100px;
  background-color: black;
}

.padding {
  padding: 0 4rem;
}

.text-red {
  color: red;
  text-transform: uppercase;
}

.padd1 {
  padding: 5px;
  width: 300px;
}

.padd {
  padding: 5px 20px;
}

.rosso {
  background-color: red;
  text-transform: uppercase;
}
</style>
