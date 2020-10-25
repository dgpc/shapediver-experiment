<template>
  <div id="app">
    <Building ticket="20f9d15ecb236b79c4c342f2714558f571d34ae17fc3678f09a4e6742f28045119010401d66d47bd2f4c0a4a5ae92be36c560606effd0a98ec6ebdcec3975a5fd947d156338ff31e4a3c142a7eb4aa864f62d3db3938be957ab118903125b434296303731c19772d5a7fc89ae42348eba26888a80fdd-75013a6ebb275765f424fa8c2b7976a5" modelViewUrl="eu-central-1" />
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
