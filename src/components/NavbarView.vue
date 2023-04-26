<template>
  <nav>
    <router-link :class="{active: $route.name == 'Home'}" to="/">MAGASIN</router-link> 
    <router-link :class="{active: $route.name == 'Cart'}" to="/cart">
      <i class="bi bi-cart-fill"></i>
    </router-link>
  </nav>
</template>

<script>
export default {
  name: 'NavbarView'
}
</script>

<style>
nav {
  padding: 10px;
  width: 100%;
  height: 30px;
  border-color: aqua;
  line-height: 30px;
  display: flex;
  justify-content: space-around;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
  text-decoration: none;
  margin: 0 5px 0 5px;
  font-size: 1.25rem;
}

.active {
  color: blue;
}
</style>
