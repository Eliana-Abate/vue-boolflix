<template>
  <div class="card">
    <ul>
      <li v-for="(item, index) in arrayFromFather" :key="index">
        {{ item.id }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "FilmCard",
  props: ["arrayFromFather"],
};
</script>

<style>
</style>