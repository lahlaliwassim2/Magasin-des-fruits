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
    <div class="no_t" :v-if=" existOrNo == true">
      aucun produit existe dans votre panier
    </div>body
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
  methods: {
    existOrNo() {
      if(this.product.lenght <= 0) {
        return true
      } return false
    }
  }
};
</script>
<style>
.cartItem {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  gap: 10px;
}


</style>