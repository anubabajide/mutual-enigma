<template>
    <div class="" style="width: 80%;  margin: 5rem auto 0 auto;">
        <img v-bind:src="product.image" 
            class="" 
            v-bind:alt="product.short_description" 
            style="width: 60%; margin: 0 auto 0 auto;"
        >
        <div class="card-body">
            <h1 class="card-title">{{ product.name }}</h1>
            <p class="text-left">Price: {{ product.price }}</p>
            <p class="text-left">Description: {{ product.description }}</p>
            <p class="text-left">Location: {{ product.location }}</p>
            <a href="#" v-on:click="broadEvent" class="btn btn-success">Show Interest</a>
        </div>
    </div>
</template>

<script>

export default {
  name: 'ProductPage',
  props: ['product'],
  methods: {
      broadEvent() {
          let vm = this.$parent
          while(vm) {
              vm.$emit('interest')
              vm = vm.$parent
          }
      }
  }
}
</script>

<style>

</style>
