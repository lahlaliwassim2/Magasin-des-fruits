<template>
    <div class="drawer-background" :class="{ show: active }" @click="$emit('close-product-drawer')" />
    <div class="drawer" :class="{ show: active }">
        <div class="drawer-close" @click="$emit('close-product-drawer')">
            X
        </div>
        <div v-if="product" class="product-details">
            <img :src="image" alt="">
            <h3 class="text-center">{{ product.name }}</h3>
            <p class="description">{{ description }}</p>
            <h3 class="text-center">{{ product.price }} DH</h3>
           <div class="flex">
            <div class="cart-total" v-if="product_total">
                <h4> Quantitée : {{ product_total }} Kg</h4>
            </div>
            <div class="prix-final" v-if="product_total">
                <h4> prix à payer  : {{ SommePrix }}</h4>
            </div>
           </div>
            <div class="button-container">
                <button class="remove" @click="removeToCart()">-</button>
                <button class="add" @click="addToCart()">+</button>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: [
        'product',
        'active'
    ],
    methods: {
        addToCart() {
            this.$store.commit('addToCart', this.product)
        },
        removeToCart() {
            this.$store.commit('removeCart', this.product)
        }
    },
    computed: {
        product_total() {
            return this.$store.getters.productQuantity(this.product)
        },
        description() {
            return this.product.descrption.substring(0, 150)
        },
        image() {
            return this.product.image
        },
        SommePrix() {
            const quant = this.$store.getters.productQuantity(this.product)
            return quant * this.product.price
        }
    }
}
</script>

<style>
    .drawer-background {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background-color: rgba(0, 0, 0, 0.6);
        z-index: 999;
        opacity: 0;
        visibility: hidden;
        transition: all 0.3s ease-in-out;
    }

    .drawer-background.show {
        opacity: 1;
        visibility: visible;
    }

    .drawer {
        position: fixed;
        top: 0;
        right: 0;
        height: 100%;
        width: 400px;
        background-color: #fff;
        z-index: 1000;
        transform: translateX(100%);
        transition: all 0.3s ease-in-out;
        overflow-y: auto;
    }

    .drawer.show {
        transform: translateX(0%);
    }

    .drawer-close {
        position: absolute;
        top: 20px;
        right: 20px;
        font-size: 1.2rem;
        cursor: pointer;
    }

    .product-details {
        padding: 20px;
    }

    .product-details img {
        width: 100%;
        height: auto;
        margin-bottom: 20px;
    }

    .product-details h3 {
        font-size: 1.5rem;
        margin-bottom: 10px;
    }

    .description {
        font-size: 1rem;
        margin-bottom: 20px;
    }

    .cart-total h4, .prix-final h4 {
        font-size: 1.2rem;
        margin-bottom: 10px;
    }

    .button-container {
        display: flex;
        justify-content: center;
        margin-top: 20px;
    }

    .button-container button {
        width: 30px;
        height: 30px;
        border: none;
        background-color: #eee;
        cursor: pointer;
        margin: 0 5px;
        font-size: 1.2rem;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .button-container button:hover {
        background-color: #ddd;
    }

    .remove {
        color:#eb8755;
    }

    .add {
        color: #00b894;
    }

    .flex {
        display: flex;
        justify-content: space-between;
        align-items: center;
    }

@media (min-width: 500px) {
    .drawer {
        width: 500px;
    }
}
</style>