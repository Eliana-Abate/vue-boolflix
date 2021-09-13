<template>
  <section class="container">
    <div>
      <h3>Movies</h3>
      <div>
        <FilmCard :arrayFromFather="arrayMovies" :typeFilm="listFilm" />
      </div>
    </div>

    <hr />
    <div>
      <h3>Serie Tv</h3>
      <div>
        <FilmCard :arrayFromFather="arraySeries" :typeFilm="listSeries" />
      </div>
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