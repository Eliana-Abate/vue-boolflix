<template>
  <section>
    <div class="row g-5" v-if="typeFilm == 'film'">
      <div class="col-4" v-for="(item, id) in arrayFromFather" :key="id">
        <div class="bool-card">
          <img :src="getCover(item.poster_path)" :alt="item.original_title" />
        </div>
      </div>
    </div>

    <!--
      <li v-for="(item, id) in arrayFromFather" :key="id">
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
        <p>
          Voto: {{ getVoteStars(item.vote_average) }}
          <span v-for="n in 5" :key="n">
            <i
              v-if="n <= getVoteStars(item.vote_average)"
              class="fas fa-star"
            ></i>
            <i v-else class="far fa-star"></i>
          </span>
        </p>
        <p>
          <img :src="getCover(item.poster_path)" :alt="item.original_title" />
        </p>
      </li> -->

    <div v-else class="row g-5">
      <div class="col-4" v-for="(item, id) in arrayFromFather" :key="id">
        <div class="bool-card">
          <img :src="getCover(item.poster_path)" :alt="item.original_name" />
        </div>
      </div>
    </div>
  </section>
  <!--<li v-for="(item, id) in arrayFromFather" :key="id">
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
        <p>
          Voto: {{ getVoteStars(item.vote_average) }}
          <span v-for="n in 5" :key="n">
            <i
              v-if="n <= getVoteStars(item.vote_average)"
              class="fas fa-star"
            ></i>
            <i v-else class="far fa-star"></i>
          </span>
        </p>
        <p>
          <img :src="getCover(item.poster_path)" :alt="item.original_name" />
        </p>
      </li> -->
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
      return stars;
    },
  },
};
</script>

<style lang='scss' scoped>
.bool-card {
  background-color: #303030;
  border: 3px solid white;
  height: 600px;
}
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}
p {
  font-weight: bold;
  color: dodgerblue;
}
span {
  font-weight: normal;
  color: black;
}
</style>