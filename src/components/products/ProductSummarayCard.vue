<template>
    <div class="card">
        <img :src="image" alt="">
        <h3>{{product.name}}</h3>
        <h5 class="price">Prix est : {{ product.price}}</h5>
        <p class="description">{{ description }}</p>
        <p class="text-muted"> {{ product.category }}</p>
        <button  class="view-product-button" @click="$emit('view-product', product)">view</button>
   </div>
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
<style lang="scss">
    .card{
        width: 80%;
        margin: 10%;
        padding: 10px;
        border-radius: 5px;
        background-color: #fff;
        box-shadow: 0 5px gray;
        img {
            width: 104%;
            height: 60%;
            }
        h5.price{
            color: gray;

        }
        p.description{
            font-size: .85rem;
        }
        p.text-muted{
            color: gray;
        }
        button.view-product-button{
            padding: 10px;
            background-color: rgb(79, 160, 187);
            border: none;
            color: wheat;
            font-weight: bold;
            border-radius: 5px;
            cursor: pointer;
        }

    }
    @media (min-width: 500px ) {
        .card{
            width: 350px;
            margin: 10px;
        }        
    }

</style>