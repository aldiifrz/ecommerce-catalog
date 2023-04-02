<template>
  <div class="product-card">
    <div class="product-image">
      <img :src="product.image" :alt="product.title" />
    </div>
    <div class="product-details">
      <h2 class="product-title">{{ product.title }}</h2>
      <p class="product-description">{{ product.description }}</p>
      <p class="product-price">{{ formattedPrice }}</p>
      <button class="buy-button">Buy Now</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "ProductCard",
  props: {
    productId: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      product: {},
    };
  },
  async created() {
    const response = await fetch(
      `https://fakestoreapi.com/products/${this.productId}`
    );
    this.product = await response.json();
  },
  computed: {
    formattedPrice() {
      return `$${(this.product.price / 100).toFixed(2)}`;
    },
  },
};
</script>

<style scoped src="@/assets/styles/product.css"></style>
