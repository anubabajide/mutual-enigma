<template>
  <div id="app">
    <Navbar/>
    <ProductList/>
  </div>
</template>

<script>

import ProductList from '@/components/ProductList.vue'
import Navbar from '@/components/Navbar.vue'

export default {
  name: 'App',
  components: {
    ProductList,
    Navbar
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 0;
}
</style>
