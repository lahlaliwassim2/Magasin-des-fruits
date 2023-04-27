<template>
  <div class="home">
   <ProductDescription
   :product="product"
   :active="active.product_drawer"
   v-on:close-product-drawer="closeproduct()"
   />
    <BannerView 
     :titre="produits"/>
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
import BannerView from '../components/BannerView.vue'
export default {
  name: 'HomeView',
  components: {
    ProductSummarayCard,
    ProductDescription,
    BannerView
},
  data () {
    return {
      items: items,
      product: null,
      active: {
        product_drawer: false,
      },
      produits : "Produts"
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
  justify-content: start;
  flex-wrap: wrap;
  gap: 10px;
}
</style>
