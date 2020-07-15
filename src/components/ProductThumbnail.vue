<template>
    <div class="card" style="width: 40%; marginBottom: 2rem">
        <img v-bind:src="product.image" 
            class="card-img-top" 
            alt="..." 
            style="width: 80%; height: 60%; margin: 0 auto 0 auto;"
        >
        <div class="card-body">
            <h5 class="card-title">{{ product.name }}</h5>
            <p class="card-text">{{ product.short_description }}</p>
            <a href="#" class="btn btn-primary">View More</a>
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
