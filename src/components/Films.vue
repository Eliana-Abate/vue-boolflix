<template>
  <section>
    <div>Qui appariranno film e serie</div>

    <FilmCard :arrayFromFather="arrayMovies" />
  </section>
</template>

<script>
import FilmCard from "@/components/FilmCard.vue";
export default {
  name: "Films",
  props: {
    arrayMovies: Array,
  },
  components: {
    FilmCard,
  },
  data() {
    return {};
  },
  methods: {},
};
</script>

<style>
</style>