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
        <p>Voto: {{ getVoteStars(item.vote_average) }}</p>
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
        <p>Voto: {{ getVoteStars(item.vote_average) }}</p>
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
      noCover: "https://www.altavod.com/assets/images/poster-placeholder.png",
      fullStar: ' `<span><i class="fas fa-star"></i></span>`',
      emptyStar: ' `<span><i class="far fa-star"></i></span> `',
    };
  },
  methods: {
    getFlag(lang) {
      return require(`@/assets/images/${lang}.png`);
    },

    getCover(cover) {
      if (cover) {
        return this.coverBasePath + cover;
      } else {
        return this.noCover;
      }
    },

    getVoteStars(vote) {
      const stars = Math.ceil(vote / 2);

      if (stars === 0) {
        return this.emptyStar.repeat(5);
      }

      if (stars === 1) {
        return this.fullStar.repeat(1) + this.emptyStar.repeat(4);
      }

      if (stars === 2) {
        return this.fullStar.repeat(2) + this.emptyStar.repeat(3);
      }

      if (stars === 3) {
        return this.fullStar.repeat(3) + this.emptyStar.repeat(2);
      }

      if (stars === 4) {
        return this.fullStar.repeat(4) + this.emptyStar.repeat(1);
      }

      if (stars === 5) {
        return this.fullStar.repeat(5) + this.emptyStar.repeat(0);
      }
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