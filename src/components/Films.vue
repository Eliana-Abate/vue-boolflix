<template>
  <section>
    <div>Qui appariranno film e serie</div>

    <FilmCard :arrayFromFather="arrayMovies" :typeFilm="listFilm" />
    <hr />
    <FilmCard :arrayFromFather="arrayMovies" :typeFilm="listSeries" />
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

<style>
</style>