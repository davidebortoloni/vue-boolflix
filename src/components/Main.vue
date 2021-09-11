<template>
  <main>
    <div class="container">
      <div class="row g-4">
        <div class="col-4" v-for="product in products" :key="product.id">
          <Product :product="product" />
        </div>
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

<style scoped lang="scss">
main {
  background-color: black;
  padding-top: 100px;
  height: 100vh;
  overflow: auto;
}
</style>
