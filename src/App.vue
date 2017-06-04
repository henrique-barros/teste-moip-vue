<template>
  <div id="app">
    <ordersList></ordersList>
  </div>
</template>

<script>
import OrdersList from './components/OrdersList'

export default {
  name: 'app',
  components: {
    OrdersList
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
