<template>
    <div class="drawer-background" :class="{show: active}" 
    @click="$emit('close-product-drawer')"
    />
    <div class="drawer" :class="{show: active}">
        <div class="drawer-close"  @click="$emit('close-product-drawer')">
            X
        </div>
        
        <div v-if="product" class="product-details">
            <img :src="image" alt="">
            <h3 class="text-center">{{ product.name }}</h3>
            <p class="description">{{ description }}</p>
            <h3 class="text-center">${{ product.price }}</h3>
            
            <div class="cart-total" v-if="product_total">
                <h3>Q:</h3>
                <h4>{{product_total}}</h4>
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
             return   this.$store.getters.productQuantity(this.product)
            },
             description() {
                return this.product.descrption.substring(0, 150)
            }
        }
    }
</script>
<style lang="scss">
.drawer-background{
    width: 100%;
    height: 100vh;
    position: fixed;
    left: 0;
    top: 0;
    background-color: rgba(134, 124, 124,0.55);
    z-index: 100;
    display: none;
    transition: display .5s;

    &.show {
        display : block;
    }
}
.drawer {
   width: 95vw;
    height: 100vh;
    background-color: #fff;
    position: fixed;
    top:0%;
    left: -105vw;
    padding:15px;
    transition: left .5s;
    z-index: 101;
    overflow: scroll;
    &.show{
        left: 0;

    }
}
.drawer-close {
    font-size: 1.5rem;
    padding: 5px;
    border-radius: 5px;
    right: 10px;
    border: 2px solid gray;
    width: 15px;
    float: right;
    cursor: pointer;
    &.hover {
        background-color: lightcoral;
    }
}
.product-details {
    display: flex;
    justify-content: center;
    flex-direction: column;
    
    p.description {
        padding: 20px;
        line-height: 1.51rem;

    }
    .button-container {
        button {
            width: 150px;
            border: none;
            padding: 10px;
            border-radius: 5px;
            margin: 0 5px 50px 5px;
            cursor: pointer;


        }
    }
}
@media (min-width: 500px) {
    .drawer {
        width : 500px;
    }
}
</style>