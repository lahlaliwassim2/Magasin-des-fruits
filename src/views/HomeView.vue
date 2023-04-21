<template>
  <div class="home">
   
    <div class="product-cards-container">
      <ProductSummarayCard
       v-for="product in items"
      :key="product.id"
      :product= "product"
       />
    </div>
  </div>
</template>

<script>
import items from '../data/items.js'
import ProductSummarayCard from '../components/products/ProductSummarayCard.vue'
export default {
  name: 'HomeView',
  components: {
    ProductSummarayCard
  },
  data () {
    return {
      items: items
    }
  }
}
</script>
<style lang="scss">
.product-cards-container {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;

}

</style>
