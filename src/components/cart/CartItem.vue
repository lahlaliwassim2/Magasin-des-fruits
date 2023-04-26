<template>
    <div class="cart-item-card">
        <div class="header">
            <img v-bind:src="image" alt="">
            <h3 class="text-sky-100">{{ product.name }}</h3>
            <h5>{{ product.quantity }}</h5>
            <h4>total : {{ item_cost }}</h4>
        </div>
        <p>{{ description }}</p>
        <button @click="remove">
            Supprimer
        </button>
    </div>
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
    width: 25%;
    height: 25%;
    margin: 5px;
    background-color: #fff;
    box-shadow: 0 0 5px gray;
    padding: 10px;
    text-align: left;
}

.header {
    display: flex;
}

.cart-item-card .header {
    display: flex;
    justify-content: space-around;
}

.cart-item-card img {
    max-width: 100%;
}

.text-sky-100 {
    color: #00BFFF;
}

img {
    width: 150px;
    height: 150px;
}

@media (min-width: 500px) {
    .cart-item-card {
        display: block;
    }
}
</style>