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
body {
  font-size: 48px;
}
tr th, td {
  padding: 8px;
  display: table-cell;
  border: 1px solid #bbbbbb;
}
th {
  font-size: 1em;
}
td {
  font-size: 0.8em;
}
</style>
