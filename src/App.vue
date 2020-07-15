<template>
  <div id="app">
    <Navbar
      v-on:product="showCrProduct"
      v-on:homepage="showHome"/>
    <ProductList
      v-show="homepage"
      v-on:interest="showCrInterest"
      :reset="reset"/>
    <CreateProduct
      v-show="crPrPage"/>
    <CreateInterest
      v-show="crInPage"/>
  </div>
</template>

<script>

import ProductList from '@/components/ProductList.vue'
import Navbar from '@/components/Navbar.vue'
import CreateProduct from '@/components/CreateProduct.vue'
import CreateInterest from '@/components/CreateInterest.vue'

export default {
  name: 'App',
  components: {
    ProductList,
    Navbar,
    CreateProduct,
    CreateInterest
  },
  data() {
    return {
      homepage: true,
      reset: true,
      crPrPage: false,
      crInPage: false
    }
  },
  methods: {
    showHome() {
      this.homepage = true
      this.reset = true
      this.crPrPage = false
      this.crInPage = false
    },
    showCrProduct() {
      this.homepage = false
      this.crPrPage = true
      this.crInPage = false
    },
    showCrInterest() {
      this.homepage = false
      this.crPrPage = false
      this.crInPage = true
    }
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
