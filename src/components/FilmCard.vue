<template>
  <div class="card">
    <ul v-if="typeFilm == 'film'">
      <li v-for="(item, index) in arrayFromFather" :key="index">
        <p>
          Titolo: <span>{{ item.title }}</span>
        </p>
        <p>
          Titolo originale: <span>{{ item.original_title }}</span>
        </p>
        <p>
          <img
            v-if="languages.includes(item.original_language)"
            :src="getFlag(item.original_language)"
            :alt="item.original_language"
          />
          <span v-else>Lingua: {{ item.original_language }}</span>
        </p>
        <p v-text="getVoteStars(item.vote_average)"></p>
        <p>
          <img :src="getCover(item.poster_path)" :alt="item.original_title" />
        </p>
      </li>
    </ul>
    <ul v-else>
      <li v-for="(item, index) in arrayFromFather" :key="index">
        <p>
          Titolo: <span>{{ item.title }}</span>
        </p>
        <p>
          Titolo originale: <span>{{ item.original_name }}</span>
        </p>
        <p>
          <img
            v-if="languages.includes(item.original_language)"
            :src="getFlag(item.original_language)"
            :alt="item.original_language"
          />
          <span v-else>Lingua: {{ item.original_language }}</span>
        </p>
        <p v-text="getVoteStars(item.vote_average)"></p>
        <p>
          <img :src="getCover(item.poster_path)" :alt="item.original_name" />
        </p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "FilmCard",
  props: ["arrayFromFather", "typeFilm"],
  data() {
    return {
      languages: ["en", "it"],
      coverBasePath: "https://image.tmdb.org/t/p/w342",
    };
  },
  methods: {
    getFlag(lang) {
      return require(`@/assets/images/${lang}.png`);
    },

    getCover(cover) {
      return this.coverBasePath + cover;
    },

    getVoteStars(vote) {
      const stars = Math.ceil(vote / 2);
      return `Voto: ${stars}`;
    },
  },
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