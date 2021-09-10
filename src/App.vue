<template>
  <div id="app">
    ciao
  </div>
</template>

<script>

import axios from 'axios';
export default {
  name: 'App',
  components: {
    
  },
  data() {
    return {
      movies: [],

    }
  }, 
  methods: {

  },
  created() {
    axios
    .get('https://api.themoviedb.org/3/search/movie/?api_key=ebe88613f786f09a75e3890c12c5547a&query=pinocchio')
    .then((res) => {
           const response = res.data.results;
                console.log(response);

                this.movies = response;  
              
    })
         
         
    
  }
}
</script>

<style lang="scss">

</style>
