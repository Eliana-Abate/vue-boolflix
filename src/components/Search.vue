<template>
  <section>
    <input type="text" v-model="searchTerm" />
    <button>Cerca</button>
  </section>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      searchTerm: "",
    };
  },

  methods: {},
};
</script>

<style>
</style>