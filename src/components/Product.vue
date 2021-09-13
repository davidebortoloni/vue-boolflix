<template>
  <div class="card">
    <img
      class="w-100 cover"
      :src="getPosterUrl()"
      :alt="`Copertina ${getTitle()}`"
    />
    <ul class="list-group">
      <li>
        <h6 class="d-inline">Titolo:</h6>
        {{ getTitle() }}
      </li>
      <li>
        <h6 class="d-inline">Titolo originale:</h6>
        {{ getOriginalTitle() }}
      </li>
      <li v-if="flags.includes(product.original_language)">
        <h6 class="d-inline">Lingua originale:</h6>
        <img
          class="language"
          :src="getFlag()"
          :alt="product.original_language"
        />
      </li>
      <li v-else>
        <h6 class="d-inline">Lingua originale:</h6>
        {{ product.original_language }}
      </li>
      <li class="vote">
        <h6 class="d-inline">Voto:</h6>
        <i v-for="(star, index) in vote" :key="index" class="fas fa-star"></i>
        <i
          v-for="(star, index) in 5 - vote"
          :key="index"
          class="far fa-star"
        ></i>
      </li>
      <li>
        <h6 class="d-inline">Trama:</h6>
        <span v-if="product.overview">
          {{ product.overview }}
        </span>
        <span v-else>
          ...
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Product",
  data() {
    return {
      flags: ["en", "it", "fr", "es"],
      flagPresent: false,
      isHover: false,
    };
  },
  computed: {
    vote() {
      return Math.round(this.product.vote_average / 2);
    },
  },
  methods: {
    getPosterUrl() {
      if (this.product.poster_path) {
        return `https://image.tmdb.org/t/p/w342${this.product.poster_path}`;
      }
      return `https://www.altavod.com/assets/images/poster-placeholder.png`;
    },
    getFlag() {
      return require(`@/assets/img/${this.product.original_language}.png`);
    },
    getTitle() {
      if (this.product.title) {
        return this.product.title;
      } else {
        return this.product.name;
      }
    },
    getOriginalTitle() {
      if (this.product.original_title) {
        return this.product.original_title;
      } else {
        return this.product.original_name;
      }
    },
  },
  props: ["product"],
};
</script>

<style scoped lang="scss">
.card {
  background-color: transparent;
  font-size: 14px;
  color: white;
  cursor: pointer;
  height: 100%;
  &:hover {
    .cover {
      display: none;
    }
    ul {
      display: inline-block;
      h6 {
        margin-right: 5px;
      }
    }
  }
  ul {
    list-style-type: none;
    display: none;
  }
}
.language {
  width: 30px;
}
.vote {
  i {
    color: gold;
  }
}
</style>
