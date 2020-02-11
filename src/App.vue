<template>
  <div id="app">
    <VehicleList />
  </div>
</template>

<script>
import VehicleList from './components/VehicleList.vue'

export default {
  name: 'App',
  components: {
    VehicleList
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
