<template>
  <div>
    <ul class="list-group">
      <li>
        <img
          class="poster"
          :src="getPosterUrl()"
          :alt="`Copertina${getTitle()}`"
        />
      </li>
      <li>Titolo: {{ getTitle() }}</li>
      <li>Titolo originale: {{ getOriginalTitle() }}</li>
      <li v-if="flags.includes(product.original_language)">
        Lingua originale:
        <img
          class="language"
          :src="getFlag()"
          :alt="product.original_language"
        />
      </li>
      <li v-else>Lingua originale: {{ product.original_language }}</li>
      <li>
        Voto:
        <i v-for="(star, index) in vote" :key="index" class="fas fa-star"></i>
        <i
          v-for="(star, index) in 5 - vote"
          :key="index"
          class="far fa-star"
        ></i>
      </li>
    </ul>
    <hr />
  </div>
</template>

<script>
export default {
  name: "Product",
  data() {
    return { flags: ["en", "it", "fr", "es"], flagPresent: false };
  },
  computed: {
    vote() {
      return Math.round(this.product.vote_average / 2);
    },
  },
  methods: {
    getPosterUrl() {
      return `https://image.tmdb.org/t/p/w342${this.product.poster_path}`;
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
.language {
  width: 40px;
}
.poster {
  width: 150px;
}
</style>
