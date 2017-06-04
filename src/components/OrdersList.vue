<template>
  <div>
    <order v-for="order in orders"
          v-bind:order="order"
          v-bind:key="order.id" />
  </div>
</template>

<script>
import Order from './Order'

export default {
  name: 'ordersList',
  components: {
    Order
  },
  data () {
    return {
      orders: [
        {
          name: "Banana",
          amount: "1",
          price: "800"
        },
        {
          name: "Heineken",
          amount: "6",
          price: "3600"
        },
        {
          name: "Toalha de banho",
          amount: "1",
          price: "1500"
        },
        {
          name: "Caixa de fósforos",
          amount: "8",
          price: "500"
        }
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
