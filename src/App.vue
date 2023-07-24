<template>
  <Header />
  <ProductCard
    v-for="(product, index) in products"
    :product="product"
    :key="index"
  />
</template>

<script>
import products from "./data/products.js";
import ProductCardVue from "./components/ProductCard.vue";
import HeaderVue from "./components/Header.vue";

export default {
  name: "App",
  components: {
    ProductCard: ProductCardVue,
    Header: HeaderVue,
  },
  data() {
    return { products };
  },
};
</script>

<style>
#app {
  font-family: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen,
    Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>
