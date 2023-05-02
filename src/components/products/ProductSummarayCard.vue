<template>
    <div 
    class="product-card" 
    v-show="isLoading"  
    >
        <div class="quat" v-if="isExist">
            {{ product_total }} 
        </div>
		<div class="product-tumb">
			<img :src="image" alt="image_fruit" style="width:100%;">
            <div class="abs" v-show="PrixHaut">
                <img src="https://d1nhio0ox7pgb.cloudfront.net/_img/g_collection_png/standard/512x512/fire.png" style="width: 20px;" alt="">
            </div>
		</div>
		<div class="product-details">
			<h4>{{ product.name }}</h4>
			<p>{{ description }}</p>
			<div class="product-bottom-details">
				<div class="product-price">{{ product.price }} dh</div>	
                <button class="btn"  @click="$emit('view-product', product)">View</button>	
			</div>
		</div>
	</div>
    <div class="product-card" v-show="!isLoading">
		<div class="product-tumb">
            chargement ...
		</div>
		<div class="product-details">
          
			<h4 class="h4">chargement ...</h4>
			<p></p>
			<div class="prod-false">
				<div class="product-price"></div>	
			</div>
		</div>
	</div>
</template>

<script>
export default {
    data() {
        return {
            isLoading: false,
            hover: false,
        }
    },

    mounted() {
    setTimeout(() => {
      this.isLoading = true;
    }, 2000);
  },
    props: ['product'],
    computed: {
        description() {
            return this.product.descrption.substring(0, 150)
        },
        image() {
            return this.product.image
        },
        PrixHaut() {
            if(this.product.price > 10 ) return true
            else return false
        },
        product_total() {
            return this.$store.getters.productQuantity(this.product)
        },
        isExist() {
            if(this.product_total > 0) {
                return true
            } else {
                return false
            }
        }
    }
}
</script>

<style>

.product-card {
    width: 380px;
    position: relative;
    box-shadow: 0 2px 7px #dfdfdf;
    margin: 50px auto;
    background: #fafafa;
}
.product-tumb {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 300px;
    background: #f0f0f0;
    position: relative;
}
.product-tumb img {
    max-width: 100%;
    max-height: 100%;
}
.product-details {
    padding: 30px;
}
.abs {
    position: absolute;
    left: 1px;
    top: 5%;
}
.product-details h4  {
    font-weight: 500;
    display: block;
    margin-bottom: 18px;
    text-transform: uppercase;
    color: #fbb72c;
    text-decoration: none;
    transition: 0.3s;
}
.product-details p {
    font-size: 15px;
    line-height: 22px;
    margin-bottom: 18px;
    color: #999;
}
.product-bottom-details {
    overflow: hidden;
    border-top: 1px solid #eee;
    padding-top: 20px;
}
.product-bottom-details div {
    float: left;
    width: 50%;
}
.product-details .h4  {
    font-weight: 500;
    display: block;
    margin-bottom: 18px;
    text-transform: uppercase;
    color: #868686;
    text-decoration: none;
    transition: 0.3s;
}
product-bottom-details .btn {
    background-color: #fbb72c;
    padding: 3px;
    width: 26%;
}
.quat{
    top: -40px;
    right: 10px;
    font-size: xx-large;
}
@media (min-width: 500px) {
    .card {
        width: 350px;
        margin: 10px;
    }
}
</style>
