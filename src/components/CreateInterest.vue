<template>
    <div class="">
        <div class="row" style="margin: 0 auto 0 auto;">
            <div style="margin: 2rem auto 0 auto;">
                <div class="card">
                    <div class="card-body" >
                        <form id="formProduct" @submit.prevent="checkForm">
                            <div class="form-group">
                                <label for='title'>Name</label>
                                <input class="form-control" type='text' name='title' id='title' v-model="title">
                            </div>
                            <div class="form-group">
                                <label for='number'>email</label>
                                <input class="form-control" type='email' name='email' id='email' v-model="email">
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
    name: 'CreateInterest',
    props: ['product'],
    data() {
        return {           
            title: null,
            email: null,
            location: null 
        }
    },
    methods:{
        checkForm() {
            axios.post(`https://mutualenigma.herokuapp.com/api/interest/`, {
                product: this.product.id,
                name: this.title,
                email: this.email,
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
