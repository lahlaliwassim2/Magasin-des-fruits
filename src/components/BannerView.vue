<template>
<div class="banner">
 <div class=" big-text">Magasin</div>
  <div>de fruits</div>
  <h3>{{ titre }}</h3>
</div>
</template>

<script>
export default {
  name : 'BannerView',
  props: {
    titre: {
      type: String,
      required: true
    }
}
}
</script>

<style>
.banner {
  width: 100%;
  background: linear-gradient(rgba(0, 0, 0, 0.253) , rgba(0, 0, 0, 0.418)),url(https://thumbs.dreamstime.com/b/vegan-food-banner-fresh-vegetables-fruits-berries-white-wooden-background-free-space-your-text-213191613.jpg);
  background-size: cover;
  font-size: 50px;
  color: #fff;
  text-align: center;
  padding: 40px 15px;
}
.big-text {
  font-size: 100px;
  font-weight: 800;
  animation-delay: 1s;
}
.banner h3 {
  display: inline-block;
  background: #e9e0e0;
  color: #eb8755;
  text-transform: uppercase;
  padding: 10px;
  text-decoration: none;
  font-size: 35px;
  border-radius: 50%;
}
</style>