<template>
  <div id="app">
    <div class="nav-bar"></div>
    <div class="product"></div>
  
    <div >
      <img  v-bind:src="image" v-bind:alt="link" />
    </div>

    <div class="product-info"></div>
    <h1>ShopRight</h1>
    <p v-for="product in products" :key="product">{{product}}</p><!-- <img alt="Vue logo" :src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
  </div>
</template>

<script> 
// import HelloWorld from './components/HelloWorld.vue'
//build your own sports jersey/ customize yiour sports jersye// slider to chansge color gradient
export default {
  name: 'App',
  components: {
    // HelloWorld
  },
  data() {
    return{
      products: ["Bottoms", "Tops", "Accessories"],
      image: require("./assets/grocery.jpg"),
      link: "hello"
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
  margin-top: 60px;
}

</style>
