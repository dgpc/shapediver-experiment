<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Building />
  </div>
</template>

<script>
import Building from './components/Building.vue'

export default {
  name: 'App',
  components: {
    Building
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
