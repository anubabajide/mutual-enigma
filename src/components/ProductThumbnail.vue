<template>
    <div class="card" style="width: 40%; marginBottom: 2rem">
        <img v-bind:src="product.image" 
            class="card-img-top" 
            v-bind:alt="product.short_description" 
            style="width: 80%; margin: 0 auto 0 auto;"
        >
        <div class="card-body">
            <h5 class="card-title">{{ product.name }}</h5>
            <p class="card-text">{{ product.short_description }}</p>
            <a href="#" v-on:click="$emit('go-to', product)" class="btn btn-success">View More</a>
        </div>
    </div>
</template>

<script>

export default {
  name: 'ProductThumbnail',
  props: ['product'],
}
</script>

<style>

</style>
