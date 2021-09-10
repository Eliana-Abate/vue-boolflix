<template>
  <div class="card">
    <ul>
      <li v-for="(item, index) in arrayFromFather" :key="index">
        <p>
          Titolo: <span>{{ item.title }}</span>
        </p>
        <p>
          Titolo originale: <span>{{ item.original_title }}</span>
        </p>
        <p>
          Lingua: <span>{{ item.original_language }}</span>
        </p>
        <p>
          Voto: <span>{{ item.vote_average }}</span>
        </p>
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

<style scoped>
p {
  font-weight: bold;
  color: dodgerblue;
}
span {
  font-weight: normal;
  color: black;
}
</style>