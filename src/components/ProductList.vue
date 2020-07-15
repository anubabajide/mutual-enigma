<template>
  <div class="">
        <div v-show="!selectedProduct||reset" style="margin: 4rem auto 0 auto;">
          <h1>Open Products</h1>
        </div>
        <ProductPage v-show="selectedProduct&&!reset" v-bind:product="selectedProduct"/>
        <div class="d-flex mx-auto" style="width: 80%;">
          <ProductThumbnail 
            class="mx-auto"
            style="padding: 2rem"
            v-on:go-to="selectedProduct = $event; reset=false"
            v-show="!selectedProduct||reset"
            v-for="product in products"
            v-bind:key="product.id" 
            v-bind:product="product"/>
        </div>
  </div>
</template>

<script>
import ProductThumbnail from '@/components/ProductThumbnail.vue'
import ProductPage from '@/components/ProductPage.vue'
import axios from 'axios'

export default {
  name: 'ProductList',
  props: {
    reset: {
      type: Boolean,
      required: false,
      default: true
    }
  },
  components: {
    ProductThumbnail,
    ProductPage
  },
  data: function() {
    return({
      products : [],
      selectedProduct: null
    })
  },
  methods: {
      getItems() {
          axios.get('https://mutualenigma.herokuapp.com/api/products/')
          .then(res => {
            this.products = res.data
            return res.data
            })
          .catch(err => console.log(err));
      }
  },
  mounted() {
    this.selectedProduct = null
  },
  created() {
    this.selectedProduct = null
    this.getItems()
  }
}
</script>

<style>

</style>
