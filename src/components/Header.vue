<template>
  <header>
    <h1>Boolflix</h1>
    <Search @inputSearch="getSearchTerm" />
    <h1>{{ searchText }}</h1>
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
    },
  },
};
</script>

<style>
</style>