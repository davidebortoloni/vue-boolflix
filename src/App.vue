<template>
  <div id="app">
    <Header @getQuery="searchProducts" />
    <main>
      <Section :products="products.movies" title="Film" />
      <Section :products="products.series" title="Serie" />
    </main>
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Section from "./components/Section.vue";

export default {
  name: "App",
  data() {
    return {
      params: {
        baseUri: "https://api.themoviedb.org/3/",
        endPoints: [
          { url: "search/movie", array: "movies" },
          { url: "search/tv", array: "series" },
        ],
        api_key: "8da4582a7a923450a3b9300a782fbf1a",
        language: "it-IT",
      },
      products: { movies: [], series: [] },
    };
  },
  components: {
    Header,
    Section,
  },
  methods: {
    searchProducts(query) {
      this.products.movies = [];
      this.products.series = [];
      if (query) {
        this.params.endPoints.forEach((endPoint) => {
          axios
            .get(`${this.params.baseUri}${endPoint.url}`, {
              params: {
                api_key: this.params.api_key,
                language: this.params.language,
                query: query,
              },
            })
            .then((res) => {
              this.products[endPoint.array] = res.data.results;
            })
            .catch((err) => {
              console.log(err);
            });
        });
      }
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
main {
  background-color: black;
  padding-top: 80px;
  height: 100vh;
  overflow: auto;
}
</style>
