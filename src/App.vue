<template>
  <div id="app">
    <Header />
    <main>
      <Films @searchedFilm="getFilmApi" />
      <h2>Stampa prop query:{{ query }}</h2>
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
      query: "",
      api: {
        baseUri: "https://api.themoviedb.org/3/search/",
        key: "ebe88613f786f09a75e3890c12c5547a",
      },
    };
  },
  methods: {
    getFilmApi(film) {
      this.movie.original_title = film;
      this.query = film;
    },
  },
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
