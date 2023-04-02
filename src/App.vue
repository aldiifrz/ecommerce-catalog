<template>
  <div class="app">
    <h1>Ecommerce App</h1>
    <div class="product-container">
      <product-card :product-id="productId[0]" v-if="currentProduct === 1" />
      <product-card :product-id="productId[1]" v-if="currentProduct === 2" />
      <div class="product-card" v-if="currentProduct === 3">
        <h2>This product is unavailable to show</h2>
      </div>
    </div>
    <div class="button-container">
      <button @click="previousProduct">Previous Product</button>
      <button @click="nextProduct">Next Product</button>
    </div>
  </div>
</template>

<script>
import ProductCard from "./components/ProductDisplay.vue";
export default {
  name: "App",
  components: {
    ProductCard,
  },
  data() {
    return {
      productId: [3, 4, 5],
      currentProduct: 1,
    };
  },
  methods: {
    previousProduct() {
      if (this.currentProduct > 1) {
        this.currentProduct--;
      }
    },
    nextProduct() {
      if (this.currentProduct < 3) {
        this.currentProduct++;
      }
    },
  },
};
</script>

<style>
@import "./assets/styles/main.css";
</style>
