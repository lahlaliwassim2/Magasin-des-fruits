<template>
  <div class="cart">
    <el-banner
      title="Mon Panier"
    />
    <el-row v-if="items && items.length > 0">
      <cart-item
        v-for="product in items"
        :key="product.id"
        :product="product"
      />
    </el-row>
    <el-row v-else>
      <el-col :span="24">
        <el-alert
          title="Votre panier est vide"
          type="warning"
          center
        />
      </el-col>
    </el-row>
    <cart-payment
      :product="product"
    />
  </div>
</template>

<script>
import { ElBanner, ElRow, ElCol, ElAlert } from 'element-plus'

import CartItem from '../components/cart/CartItem.vue'
import CartPayment from '../components/cart/CartPayment.vue'

export default {
  components: {
    ElBanner,
    ElRow,
    ElCol,
    ElAlert,
    CartItem, 
    CartPayment
  },
  data () {
    return {
      err : "Votre panier est vide"
    }
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
.cart-item {
  display: grid;
  grid-template-columns: repeat(3, 2fr);
  grid-gap: 54px;
}
.titre {
  font-size: 25px;
}
@media (max-width: 500px) {
  .cart-item {
    display: block;
  }
}
</style>
