<template>
    <div class="">
        <div class="row">
            <div style="margin: 2rem auto 0 auto;">
                <div class="card">
                    <div class="card-body">
                        <form id="formProduct" @submit.prevent="checkForm">
                            <div class="form-group">
                                <label for='title'>Title</label>
                                <input class="form-control" type='text' name='title' id='title' v-model="title">
                            </div>
                            <div class="form-group">
                                <label for='number'>Price</label>
                                <input class="form-control" type='number' name='price' id='price' v-model="price">
                            </div>
                            <div class="form-group">
                                <label for='shortDescription'>Short Description</label>
                                <input class="form-control" type='textarea' name='shortDescription' id='shortDescription' v-model="shortDescription">
                            </div>
                            <div class="form-group">
                                <label for='descriptions'>Detailed Description</label>
                                <input class="form-control" type='textarea' name='descriptions' id='description' v-model="descriptions">
                            </div>
                            <div class="form-group">
                                <!-- <BaseInput label="input" value="image" v-model="input"/> -->
                                <label>Upload File
                                    <input class="form-control" type="file" id="file" ref="file" v-on:change="handleFileUpload()">
                                </label>
                            </div>
                            <div class="form-group">
                                <label for='location'>Location</label>
                                <input class="form-control" type='text' name='location' id='location' v-model="location">
                            </div>
                            <button type="submit" class="btn btn-primary">Submit</button>
                        </form>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
import axios from 'axios'

export default {
    // components: [
    // ],
    name: 'CreateProduct',
    data() {
        return {           
            title: null,
            price: null,
            descriptions: null,
            shortDescription: null,
            image: null,
            location: null 
        }
    },
    methods:{
        handleFileUpload() {
            this.file = this.$refs.file.files[0];
        },
        checkForm() {
            axios.post(`${process.env.VUE_APP_BASE_URL}/api/products/`, {
                user: localStorage.getItem("user-id"),
                name: this.title,
                price: this.price,
                description: this.descriptions,
                short_description: this.shortDescription,
                image: this.file,
                location: this.location 
            })
            .then(res => console.log(res))
            .catch(res => console.log(res))
        }
    }
}
</script>

<style>

</style>
