<template>
  <header>
    <h1>Boolflix</h1>
    <Search @inputSearch="getSearchTerm" />
  </header>
</template>

<script>
import Search from "@/components/Search.vue";
export default {
  name: "Header",
  components: {
    Search,
  },
  data() {
    return {
      searchText: "",
    };
  },
  methods: {
    getSearchTerm(search) {
      this.searchText = search;
      this.$emit("searchedFilm", this.searchText);
    },
  },
};
</script>

<style>
</style>