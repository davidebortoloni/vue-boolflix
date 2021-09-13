<template>
  <section class="py-5">
    <div class="container">
      <h2 class="text-white my-4">{{ title }}</h2>
      <div v-if="products[0]" class="row g-4">
        <div
          class="col-3"
          v-for="(product, index) in products"
          :key="product.id + '-' + index"
        >
          <Product :product="product" />
        </div>
      </div>
      <div v-else>
        <h3>Non sono stati trovati titoli</h3>
      </div>
    </div>
  </section>
</template>

<script>
import Product from "./Product.vue";

export default {
  name: "Section",
  components: {
    Product,
  },
  props: ["products", "title"],
};
</script>

<style scoped lang="scss">
section {
  border-top: 3px solid rgb(229, 9, 20);
}
</style>
