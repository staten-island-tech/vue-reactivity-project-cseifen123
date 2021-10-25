<template>
  <div id="app">
    <H1> Meals Selection App</H1>
    <mealsSelection/>
  </div>
</template>

<script>

import mealsSelection from './components/mealsSelection.vue'
export default {
  name: 'App',
  components: {
  mealsSelection
   
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

