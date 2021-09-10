<template>
  <main>
    <div>
      <div v-for="product in products" :key="product.id">
        <Product :product="product" />
      </div>
    </div>
  </main>
</template>

<script>
import Product from "./Product.vue";

export default {
  name: "Main",
  components: {
    Product,
  },
  props: ["products"],
};
</script>

<style scoped lang="scss"></style>
