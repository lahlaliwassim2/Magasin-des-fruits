<template>
  <div>
    <NavbarView />
    <router-view />
  </div>
</template>

<script>
import NavbarView from './components/NavbarView.vue'

export default {
  name: 'App',
  components: {
    NavbarView
  },
  mounted() {
    this.$store.commit('UpdateFromLocalStorage')
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

html, body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
  box-sizing: border-box;
}
body {
  background-color: rgb(245, 245, 245);
}

</style>
