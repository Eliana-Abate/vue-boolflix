<template>
  <header>
      <h1>Boolflix</h1>
      <Search/>

  </header>
</template>

<script>
import Search from '@/components/Search.vue';
export default {
    name: 'Header',
    components: {
        Search,
    },

}
</script>

<style>

</style>