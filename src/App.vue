<template>
  <div id="app">
    <grocery-list/>
  </div>
</template>

<script>
import groceryList from './components/groceryList.vue'

export default {
  name: 'App',
  components: {
    groceryList
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
