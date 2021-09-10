<template>
  <section>
    <div>Qui appariranno film e serie</div>
    <FilmCard />
  </section>
</template>

<script>
import FilmCard from "@/components/FilmCard.vue";
export default {
  name: "Films",
  components: {
    FilmCard,
  },
  methods: {},
};
</script>

<style>
</style>