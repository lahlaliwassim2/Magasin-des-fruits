<template>
  <div class="cart ">
    <BannerView 
    titre="Mon Panier"
    />
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

import BannerView from '@/components/BannerView.vue';
import CartItems from '../components/cart/CartItem.vue'
import CartPayment from '../components/cart/CartPayment.vue'

export default {
    components: {
    CartItems,
    CartPayment,
    BannerView
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
.cart {
  display: flex;
  flex-direction: column;
}
.cartItem {
 display: grid;
 grid-template-columns: repeat(3, 2fr);
  grid-gap: 54px;
}
.titre {
  font-size: 25px;
}
</style>