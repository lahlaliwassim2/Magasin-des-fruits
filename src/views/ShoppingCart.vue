<template>
  <div class="cart ">
    <h1>My Cart</h1>
    <!-- <div v-for="product in items" :key="product.id">
      {{ product.name }}
    </div> -->
    <div class="cartItem">
    <CartItems 
    v-for="(product) in items" 
    :key="product.id"
    :product="product"
    />
</div>

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
<style>
.cartItem {
  display: flex;
    gap: 51px;
}
</style>