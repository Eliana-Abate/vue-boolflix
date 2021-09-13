<template>
  <section>
    <div class="row g-5" v-if="typeFilm == 'film'">
      <div class="col-4" v-for="(item, id) in arrayFromFather" :key="id">
        <div class="bool-card">
          <img :src="getCover(item.poster_path)" :alt="item.original_title" />

          <!-- Hover effect -->
          <div class="hover-effect">
            <p>Titolo: {{ item.title }}</p>
            <p>Titolo originale: {{ item.original_title }}</p>

            <p>
              <img
                class="flag"
                v-if="languages.includes(item.original_language)"
                :src="getFlag(item.original_language)"
                :alt="item.original_language"
              />
              <span class="other-lang" v-else
                >Lingua: {{ item.original_language }}</span
              >
            </p>

            <p>
              Voto:
              <span v-for="n in 5" :key="n">
                <i
                  v-if="n <= getVoteStars(item.vote_average)"
                  class="fas fa-star"
                ></i>
                <i v-else class="far fa-star"></i>
              </span>
            </p>

            <p>{{ item.overview }}</p>
          </div>
        </div>
      </div>
    </div>

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
  border: 3px solid white;
  height: 600px;
}

img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}

.hover-effect {
  height: 100%;
  padding: 30px;
  background-color: black;
  color: white;
  font-size: 1.1em;
  overflow-y: auto;
  display: none;
  .flag {
    width: 30px;
    height: 20px;
  }
  .other-lang {
    color: red;
  }
}

span {
  font-weight: normal;
  color: rgb(255, 208, 0);
}

.bool-card:hover > img {
  display: none;
}

.bool-card:hover > .hover-effect {
  display: block;
}
</style>