<template>
  <div>
    <ul>
      <li>{{ product.title }}</li>
      <li>{{ product.original_title }}</li>
      <li>{{ product.original_language }}</li>
      <li>{{ product.vote_average }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Product",
  props: ["product"],
};
</script>

<style scoped lang="scss"></style>
