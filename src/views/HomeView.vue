<template>
  <div class="home">
   <ProductDescription
   :product="product"
   :active="active.product_drawer"
   v-on:close-product-drawer="closeproduct()"
   />

    <div class="product-cards-container">
      <ProductSummarayCard
       v-for="product in items"
      :key="product.id"
      :product= "product"
      v-on:view-product="viewProduct($event)"
       />
    </div>
  </div>
</template>

<script>
import items from '../data/items.js'
import ProductDescription from '../components/products/ProductDescription.vue'
import ProductSummarayCard from '../components/products/ProductSummarayCard.vue'
export default {
  name: 'HomeView',
  components: {
    ProductSummarayCard,
    ProductDescription
  },
  data () {
    return {
      items: items,
      product: null,
      active: {
        product_drawer: false,
      }
    }
  },
  methods: {
    viewProduct(product) {
      this.product = product
      this.active.product_drawer = true
      console.log(this.product)
    },
    closeproduct() {
      this.active.product_drawer = false
    }
  }
}
</script>
<style>
.product-cards-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-evenly;
  gap: 10px;
}


</style>
