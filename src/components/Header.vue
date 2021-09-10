<template
  ><header>
    <Search @getQuery="getQuery" />
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

<style scoped lang="scss"></style>
