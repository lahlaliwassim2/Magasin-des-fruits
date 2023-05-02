<template>
  <el-card class="cart-item-card ">
    <div class="header">
      <img :src="image" alt="">
      <h3>{{ product.name }}</h3>
      <h5>{{ product.quantity }} Kg</h5>
      <h4>total : {{ item_cost }} Dh</h4>
    </div>
    <el-button type="danger" @click="remove">Supprimer</el-button>
  </el-card>
</template>

<script>
export default {

    props: ['product'],
    computed: {
        item_cost() {
            return this.product.price * this.product.quantity
        },
        image() {
            return this.product.image
        }

    },
    methods: {
        remove() {
            this.$store.commit('deleteProductFromCart', this.product)
        }
    }
}
</script>

<style >
.cart-item-card {
  border: 1px solid #ddd;
  border-radius: 8px;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
  padding: 16px;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  margin: 1px;
}

.cart-item-card .header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 16px;
}

.cart-item-card .header img {
  width: 80px;
  height: 80px;
  object-fit: cover;
  margin-right: 16px;
}

.cart-item-card h3,
.cart-item-card h4,
.cart-item-card h5 {
  margin: 0;
}

.cart-item-card h3 {
  font-size: 24px;
  color: #333;
}

.cart-item-card h4 {
  font-size: 20px;
  color: #333;
}

.cart-item-card h5 {
  font-size: 16px;
  color: #888;
}

.cart-item-card p {
  font-size: 16px;
  line-height: 1.5;
  color: #555;
  margin-bottom: 16px;
}

.cart-item-card button {
  background-color: #f44336;
  color: #fff;
  border: none;
  border-radius: 4px;
  padding: 8px 16px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

.cart-item-card button:hover {
  background-color: #d32f2f;
}

.cart-item-card .header h4 {
  font-weight: bold;
  font-size: 24px;
  color: #333;
}

@media (min-width: 500px) {
    .cart-item-card {
        display: block;
    }
}
</style>