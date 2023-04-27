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
<div v-if="items.length <= 0">
      <ErrorView 
      :message="err "
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
import ErrorView from '../components/cart/ErrorView.vue'

export default {
  data () {
    return {
      err : "Votre panier est vide"
    }
  },
    components: {
    CartItems,
    CartPayment,
    BannerView,
    ErrorView
},
  computed: {
    items() {
      return this.$store.getters.cartItems;
    },
  },
  methods: {
    existOrNo() {
      if(this.items.lenght <= 0) {
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
@media (max-width: 500px) {
    .cartItem {
       display: block;
    }
}
</style>