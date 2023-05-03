<template>
  <div class="home">
   <ProductDescription 
   :product="product"
   :active="active.product_drawer"
   @close-product-drawer="closeproduct()">
   </ProductDescription>
    <BannerView  
     :titre="produits">
    </BannerView>
    <div class="product-cards-container">
      <ProductSummarayCard 
       v-for="product in items"
       :key="product.id"
       :product= "product"
       @view-product="viewProduct($event)">
      </ProductSummarayCard>
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
      produits : "PRODUITS"
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
