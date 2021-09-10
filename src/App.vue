<template>
  <div id="app">
    <Header />
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
export default {
  name: "App",
  components: {
    Header,
  },
  data() {
    return {
      movies: [],
      query: "",
      api: {
        baseUri: "https://api.themoviedb.org/3/search/",
        key: "ebe88613f786f09a75e3890c12c5547a",
      },
    };
  },
  methods: {},
  created() {
    axios
      .get(
        `${this.api.baseUri}movie/?api_key=${this.api.key}&query=${this.query}`
      )
      .then((res) => {
        const response = res.data.results;
        console.log(response);

        this.movies = response;
      });
  },
};
</script>

<style lang="scss">
</style>
