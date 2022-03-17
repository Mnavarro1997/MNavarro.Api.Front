<template>
  <div id="app">
    <div id="nav">
      <router-link to="/" style="text-decoration: none; margin-left: 300px;font-family: verdana; font-size: 30px">ECOMMERCE</router-link>
      <router-link to="/cart" style="text-decoration: none; margin-left: 630px;font-family: verdana; font-size: 18px">Carrito</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>
import api_url from './utils/api'

export default {

  created(){
    fetch(api_url('/products'))
  },

  computed: {
    isMock() {
      return process.env.VUE_APP_API_IS_MOCK === "true"
    }
  }
}
</script>

<style>
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  background-color: grey;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: black;
}

#nav a.router-link-exact-active {
  color: black;
}
</style>
