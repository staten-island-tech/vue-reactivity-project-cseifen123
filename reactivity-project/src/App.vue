<template>
  <div id="app">
    <div class="product">
      <div class="product-image">
        <img  v-bind:src="image" />
      </div>
    </div>

    <div class="product-info">
      <h1>ShopRight</h1>
      <p v-for="product in products" :key="product">{{product}}</p> <!--creates a div for each product-->
      <p v-if="inStock">In Stock</p>
      <p v-else>Out of Stock</p>
      <div v-for="variant in variants" :key="variant">
        <p>{{variant.variantColor}}</p>
      </div>
    </div>
    <!-- <p v-if="inStock">In Stock</p>
    <p v-else>Out of Stock</p> -->
   
    <!-- <span v-show="onSale">On sale!</span> -->
<!-- <img alt="Vue logo" :src="./assets/logo.png">
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
      inStock: true,
      details: ["80% cotton", "20% polyester"],
      variants:[
        {
          varriantId: 2234,
          variantColor: "green"
        },
        {
          variantId: 2235,
          variantColor: "blue"
        }
      ]
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
