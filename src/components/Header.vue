<template>
  <header class="px-5">
    <div class="row h-100">
      <div class="col-6 d-flex align-items-center">
        <h1 class="display-5">BOOLFLIX</h1>
      </div>
      <div class="col-6 d-flex align-items-center justify-content-end">
        <Search @inputSearch="getSearchTerm" />
      </div>
    </div>
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

<style lang="scss" scoped>
header {
  height: 80px;
  background-color: black;
  font-family: "Bebas Neue", cursive;
  color: #e50914;
  h1 {
    margin: 0;
  }
}
</style>