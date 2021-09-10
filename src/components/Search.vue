<template>
  <div>
    <input type="text" v-model="query" placeholder="Scrivi qui..." />
    <button type="button" @click="getQuery">Cerca</button>
  </div>
</template>

<script>
export default {
  name: "Search",
  data() {
    return {
      query: "",
    };
  },
  methods: {
    getQuery() {
      if (this.query) {
        this.$emit("getQuery", this.query);
      }
    },
  },
};
</script>

<style scoped lang="scss"></style>
