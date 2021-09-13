<template>
  <section class="container">
    <div>
      <h3 class="py-3">Movies</h3>
      <div v-if="arrayMovies == ''">
        <p class="y-msg">Non sono presenti Film nella lista...</p>
        <p>Effettua una nuova ricerca per questa categoria.</p>
      </div>
      <FilmCard v-else :arrayFromFather="arrayMovies" :typeFilm="listFilm" />
    </div>

    <div class="pt-5">
      <h3 class="py-3">Serie Tv</h3>
      <div v-if="arraySeries == ''">
        <p class="y-msg">Non sono presenti Serie TV nella lista...</p>
        <p>Effettua una nuova ricerca per questa categoria.</p>
      </div>

      <FilmCard v-else :arrayFromFather="arraySeries" :typeFilm="listSeries" />
    </div>
  </section>
</template>

<script>
import FilmCard from "@/components/FilmCard.vue";
export default {
  name: "Films",
  props: {
    arrayMovies: Array,
    arraySeries: Array,
  },
  components: {
    FilmCard,
  },
  data() {
    return {
      listFilm: "film",
      listSeries: "series",
    };
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
.y-msg {
  color: rgb(255, 208, 0);
}
</style>