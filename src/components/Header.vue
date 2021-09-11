<template>
  <header class="p-4 w-100">
    <div class="container">
      <div class="row justify-content-between">
        <div class="col-auto">
          <h1>BOOLFLIX</h1>
        </div>
        <div class="col-auto">
          <Search @getQuery="getQuery" />
        </div>
      </div>
    </div>
  </header>
</template>

<script>
import Search from "./Search.vue";

export default {
  name: "Headers",
  components: {
    Search,
  },
  methods: {
    getQuery(query) {
      this.$emit("getQuery", query);
    },
  },
};
</script>

<style scoped lang="scss">
header {
  position: fixed;
  background-color: black;
  z-index: 1;
}
h1 {
  color: rgb(229, 9, 20);
}
</style>
