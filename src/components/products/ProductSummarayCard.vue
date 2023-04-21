<template>
    <div class="card">
        <h3>{{product.name}}</h3>
        <h5 class="price">Prix est : ${{ product.price}}</h5>
        <p class="description"> </p>
    </div>
</template>
<script>
    export default {
        props: ['product']
    }
</script>