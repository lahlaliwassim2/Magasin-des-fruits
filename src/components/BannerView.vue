<template>
<div class="banner animated tada">
 <div class=" big-text animated tada">Magasin</div>
  <div>de fruits</div>
  <a href="#">Panier</a>
</div>
</template>
<style>
.banner {
  width: 100%;
  background: linear-gradient(rgba(0, 0, 0, 0.253) , rgba(0, 0, 0, 0.418)),url(https://thumbs.dreamstime.com/b/vegan-food-banner-fresh-vegetables-fruits-berries-white-wooden-background-free-space-your-text-213191613.jpg);
  background-size: cover;
  font-size: 80px;
  color: #fff;
  text-align: center;
  padding: 40px 15px;
}

.big-text {
  font-size: 130px;
  font-weight: 800;
  animation-delay: 1s;
}
.banner a {
  display: inline-block;
  background: #fff;
  color: #36465d;
  text-transform: uppercase;
  padding: 15px;
  text-decoration: none;
  font-size: 40px;
  transition: 0.3s;
}
.banner a:hover {
  background: #333;
  color: #fff;
  padding: 15px 20px;
}

</style>