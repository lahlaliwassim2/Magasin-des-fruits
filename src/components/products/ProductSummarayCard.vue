<template>
  <el-card v-show="isLoading" class="product-card">
    <div v-if="isExist" class="quat">{{ product_total }}</div>
    <div class="product-tumb">
      <img :src="image" alt="image_fruit" style="width:100%;" />
      <el-badge v-show="PrixHaut"  class="abs">
        <img
          src="https://d1nhio0ox7pgb.cloudfront.net/_img/g_collection_png/standard/512x512/fire.png"
          style="width: 20px;"
          alt=""
        />
      </el-badge>
    </div>
    <div class="product-details">
      <h4>{{ product.name }}</h4>
      <p>{{ description }}</p>
      <div class="product-bottom-details">
        <div class="product-price">{{ product.price }} dh</div>
        <el-button class="btn" @click="$emit('view-product', product)">View</el-button>
      </div>
    </div>
  </el-card>
  <el-skeleton v-show="!isLoading" style="width: 240px">
    <template #template>
      <el-skeleton-item variant="image" style="width: 240px; height: 240px" />
      <div style="padding: 14px">
        <el-skeleton-item variant="p" style="width: 50%" />
        <div
          style="
            display: flex;
            align-items: center;
            justify-items: space-between;
          "
        >
          <el-skeleton-item variant="text" style="margin-right: 16px" />
          <el-skeleton-item variant="text" style="width: 30%" />
        </div>
      </div>
    </template>
  </el-skeleton>
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
    box-shadow: 0 2px 7px #ffffff;
    margin: 50px auto;
    background: #fafafa;
}
.product-tumb {
    display: flex;
    flex-direction: column-reverse;
    justify-content: space-between;
    height: 300px;
    background: #ffff;
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
