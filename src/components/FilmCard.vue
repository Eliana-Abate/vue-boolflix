<template>
  <div class="card">
    <ul>
      <li v-for="(item, index) in allMovies" :key="index">
        {{ item.id }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "FilmCard",
  props: "allMovies",
};
</script>

<style>
</style>