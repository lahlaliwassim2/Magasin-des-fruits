<template>
    <button class="view-product-button" @click="$emit('view-product', product)">
        <div class="card bg-gray-900">
            <h3>{{product.name}}</h3>
            <img :src="image" alt="">
            <h5 class="price">Prix est : {{ product.price}}</h5>
            <p class="description">{{ description }}</p>
            <p class="text-muted"> {{ product.category }}</p>
        </div>
    </button>
</template>

<script>
    export default {
        props: ['product'],

        computed: {
            description() {
                return this.product.descrption.substring(0, 150)
            },
            image() {
                return this.product.image
            }
        }
    }
</script>

<style>
    .card {
        width: 80%;
        margin: 10%;
        padding: 10px;
        border-radius: 5px;
        background-color: #fff;
        box-shadow: 0 5px gray;
    }

    .card img {
        width: 100%;
        height: 60%;
    }

    .card h5.price {
        color: gray;
    }

    .card p.description {
        font-size: .85rem;
    }

    .card p.text-muted {
        color: gray;
    }

    button.view-product-button {
        padding: 10px;
        border: none;
        color: wheat;
        font-weight: bold;
        border-radius: 5px;
        cursor: pointer;
    }

    @media (min-width: 500px) {
        .card {
            width: 350px;
            margin: 10px;
        }
    }
</style>
