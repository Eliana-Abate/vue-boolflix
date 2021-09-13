<template>
  <section class="container">
    <div>
      <h3 class="py-3">Movies</h3>

      <FilmCard :arrayFromFather="arrayMovies" :typeFilm="listFilm" />
    </div>

    <div class="pt-5">
      <h3 class="py-3">Serie Tv</h3>

      <FilmCard :arrayFromFather="arraySeries" :typeFilm="listSeries" />
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
</style>