<template>
  <div class="">
        <div style="margin: 4rem auto 0 auto;">
          <h1>Open Products</h1>
        </div>
        <div class="d-flex mx-auto" style="width: 80%;">
          <ProductThumbnail 
            class="mx-auto"
            style="padding: 2rem"
            v-for="product in products"
            v-bind:key="product" 
            v-bind:product="product"/>
        </div>
  </div>
</template>

<script>
import ProductThumbnail from '@/components/ProductThumbnail.vue'
import axios from 'axios'

export default {
  name: 'ProductList',
  components: {
    ProductThumbnail  
  },
  data: function() {
    return({
      products : []
    })
  },
  methods: {
      getItems() {
          axios.get('http://127.0.0.1:8000/api/products/')
          .then(res => {
            this.products = res.data
            return res.data
            })
          .catch(err => console.log(err));
      }
  },
  mounted() {
    this.getItems()
  }
}
</script>

<style>

</style>
