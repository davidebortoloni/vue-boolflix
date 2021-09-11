<template>
  <div class="input-group mb-3">
    <input
      type="text"
      class="form-control"
      v-model="query"
      placeholder="Scrivi qui..."
    />
    <button class="btn btn-outline-danger" type="button" @click="getQuery">
      Cerca
    </button>
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
