<template>
    <div>
        <b-navbar toggleable="lg" type="dark" variant="info">
            <b-navbar-brand href='#' @click="$emit('homepage')">Mutual Enigma</b-navbar-brand>

            <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>

            <b-collapse id="nav-collapse" is-nav>

                <b-navbar-nav class="">
                    <b-nav-form v-if="!token" @submit.prevent="login">
                        <b-form-input id="username" name="username" size="sm" class="mr-sm-2" placeholder="Username" v-model="username"></b-form-input>
                        <b-form-input id="password" name="password" type="password" size="sm" class="mr-sm-2" placeholder="Password" v-model="password"></b-form-input>
                        <b-button size="sm" class="my-2 my-sm-0" type="submit">Login</b-button>
                    </b-nav-form>

                    <b-nav-item-dropdown v-if="token" right>
                        <template v-slot:button-content>
                            <em>User</em>
                        </template>
                        <b-dropdown-item href="#" @click="$emit('product')">Create Product</b-dropdown-item>
                        <b-dropdown-item href="#" v-on:click="logout">Sign Out</b-dropdown-item>
                    </b-nav-item-dropdown>
                </b-navbar-nav>
            </b-collapse>
        </b-navbar>
    </div>
</template>

<script>
import axios from 'axios'

export default {
  name: 'NavBar',
  data() {
      return {
          username: null,
          password: null,
          token: localStorage.getItem('user-token')
      }
  },
  methods: {
      login() {
          axios.post(`http://localhost:8000/auth/`, {
             username: this.username,
             password: this.password 
          })
          .then(res => {
              this.token = res.data.token
            //   console.log(res)
              localStorage.setItem('user-token', res.data.token)
              localStorage.setItem('user-id', res.data.id)
            })
          .catch(() => {
              localStorage.removeItem('user-token')
              this.token = null
          })
      },
      logout() {
          localStorage.removeItem('user-token')
          this.token = null
      }
  }
}
</script>

<style>

</style>
