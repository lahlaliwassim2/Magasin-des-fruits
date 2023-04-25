<template>
    <div class="cart-item-card">
        <div class="header">
            <img v-bind:src="image" alt="">
            <h3>{{ product.name }}</h3>
            <h5>{{ product.quantity }}</h5>
            <h4>total : {{ item_cost }}</h4>
        </div>
            <p>{{ description }}</p>
    </div>
</template>

<script>
export default {
   
    props: ['product'],
    computed: { description() {
            return this.product.description
        }
        ,
        item_cost() {
            return this.product.price * this.product.quantity
        },
       
    }
}
</script>
<style lang="scss">
.cart-item-card {
    width: 90%;
    margin: 5%;
    background-color: #fff;
    box-shadow: 0 0 5px gray;
    padding: 10px;
    text-align: left;

    .header {
        display: flex;
        justify-content: space-around;
    }
}
</style>