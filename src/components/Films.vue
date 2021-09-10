<template>
  <section>
    <div>Qui appariranno film e serie</div>

    <FilmCard :allMovies="arrayMovies" />
  </section>
</template>

<script>
import FilmCard from "@/components/FilmCard.vue";
export default {
  name: "Films",
  props: ["arrayMovies"],
  components: {
    FilmCard,
  },
  methods: {},
};
</script>

<style>
</style>