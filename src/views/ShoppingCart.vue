<template>
  <div>
    <h1>My Cart</h1>
    <!-- <div v-for="product in items" :key="product.id">
      {{ product.name }}
    </div> -->
    <CartItems 
    v-for="(product) in items" 
    :key="product.id"
    :product="product"
    />


    <CartPayment 
      :product="product"
    />

  </div>
</template>
<script>
import CartItems from '../components/cart/CartItem.vue'
import CartPayment from '../components/cart/CartPayment.vue'

export default {
    components: {
    CartItems,
    CartPayment
    },
  computed: {
    items() {
      return this.$store.getters.cartItems;
    },
  },
};
</script>
