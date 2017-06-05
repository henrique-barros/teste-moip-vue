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
  font-family: 'Quicksand';
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1 {
  font-size: 36px;
}
h2 {
  font-size: 24px;
}
h3 {
  font-size: 18px;
}
h4 {
  font-size: 16px;
}
h5 {
  font-size: 14px;
}
h6 {
  font-size: 12px;
  font-weight: bold;
  text-transform: uppercase;
}
body {
  font-size: 16px;
  background-color: lightblue;
}
grid-item {
  text-align: left;
}

@media (max-width: 480px) {
  h1 {
    font-size: 24px;
  }
  h2 {
    font-size: 18px;
  }
  h3 {
    font-size: 16px;
  }
  h4 {
    font-size: 14px;
  }
  h5 {
    font-size: 12px;
  }
  h6 {
    font-size: 10px;
    font-weight: bold;
    text-transform: uppercase;
  }
}
</style>
