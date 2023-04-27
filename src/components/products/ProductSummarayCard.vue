<template>
    <!-- <button class="view-product-button" @click="$emit('view-product', product)">
        <div class="card ">
            <h3 class="text-muted bg-gray-600">{{ product.name }}</h3>
            <img class="card-img" :src="image" alt="">
            <h5 class="price">Prix est : {{ product.price }}</h5>
            <p class="description">{{ description }}</p>
        </div>
    </button> -->
    <div class="product-card">
		
		<div class="product-tumb">
			<img :src="image" alt="" style="width:100%;">
		</div>
		<div class="product-details">
			<h4><a href="">{{ product.name }}</a></h4>
			<p>{{ description }}</p>
			<div class="product-bottom-details">
				<div class="product-price">{{ product.price }} dh</div>	
                <button @click="$emit('view-product', product)">View</button>	
			</div>
		</div>
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

<style>

a
{
    text-decoration: none;
}
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
    padding: 50px;
    background: #f0f0f0;
}

.product-tumb img {
    max-width: 100%;
    max-height: 100%;
}

.product-details {
    padding: 30px;
}
.product-details h4 a {
    font-weight: 500;
    display: block;
    margin-bottom: 18px;
    text-transform: uppercase;
    color: #363636;
    text-decoration: none;
    transition: 0.3s;
}

.product-details h4 a:hover {
    color: #fbb72c;
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



@media (min-width: 500px) {
    .card {
        width: 350px;
        margin: 10px;
    }
}
</style>
