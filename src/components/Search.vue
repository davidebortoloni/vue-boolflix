<template>
  <div class="input-group mb-3">
    <input
      type="text"
      class="form-control"
      v-model="query"
      :placeholder="placeholder"
      @keyup.enter="getQuery"
    />
    <button class="btn btn-outline-danger" type="button" @click="getQuery">
      {{ buttonContent }}
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
  props: ["placeholder", "buttonContent"],
  methods: {
    getQuery() {
      this.$emit("getQuery", this.query);
    },
  },
};
</script>

<style scoped lang="scss"></style>
