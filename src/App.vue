<template>
  <div id="app">
    <Header @searchedFilm="getFilmApi" />
    <main class="py-5">
      <Films :arrayMovies="movies" :arraySeries="series" />
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Header from "@/components/Header.vue";
import Films from "@/components/Films.vue";
export default {
  name: "App",
  components: {
    Header,
    Films,
  },
  data() {
    return {
      movies: [],
      series: [],
      api: {
        baseUri: "https://api.themoviedb.org/3/",
        endpoint: "search/",
        key: "ebe88613f786f09a75e3890c12c5547a",
      },
    };
  },
  methods: {
    getFilmApi(query) {
      console.log(query);
      axios
        .get(
          this.api.baseUri +
            this.api.endpoint +
            "movie/?api_key=" +
            this.api.key +
            "&query=" +
            query
        )

        .then((res) => {
          const response = res.data.results;
          console.log(res.data);

          this.movies = response;
        });
      axios
        .get(
          this.api.baseUri +
            this.api.endpoint +
            "tv/?api_key=" +
            this.api.key +
            "&query=" +
            query
        )

        .then((res) => {
          const response = res.data.results;
          console.log(res.data);

          this.series = response;
        });
    },
  },
};
</script>

<style lang="scss">
@import "./assets/scss/style.scss";
</style>
