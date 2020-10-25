<template>
  <div id="app">
    <Building ticket="4a01c613c39e63883dee8107e64fd99b8f095dca20981be5b6772c0e5b30fae23b6736844433634fe1edfb2042c622d69e6b1b6a07766a2eb92cc942c61cd786bfd9ba6a269e477cc4be297844c770741247b211c02b0674f09e87daab7e86ad9ee870968fe51c1a33ef8c78f0fcfac140e1b181df51" modelViewUrl="eu-central-1" />
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
