<template>
  <div id="app">
    <Header @getQuery="searchProduct" />
    <Main :products="products" />
  </div>
</template>

<script>
import axios from "axios";
import Header from "./components/Header.vue";
import Main from "./components/Main.vue";

export default {
  name: "App",
  data() {
    return {
      params: {
        baseUri: "https://api.themoviedb.org/3/",
        endPoints: ["search/movie/?", "search/tv/?"],
        api_key: "8da4582a7a923450a3b9300a782fbf1a",
        language: "it-IT",
      },
      products: [],
    };
  },
  components: {
    Header,
    Main,
  },
  methods: {
    searchProduct(query) {
      this.products = [];
      this.params.endPoints.forEach((endPoint) => {
        axios
          .get(`${this.params.baseUri}${endPoint}`, {
            params: {
              api_key: this.params.api_key,
              language: this.params.language,
              query: query,
            },
          })
          .then((res) => {
            this.products = [...this.products, ...res.data.results];
          })
          .catch((err) => {
            console.log(err);
          });
      });
    },
  },
};
</script>

<style lang="scss">
@import "~bootstrap/scss/bootstrap";
</style>
