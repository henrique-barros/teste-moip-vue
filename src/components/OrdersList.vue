<template>
  <div>
    <p>Lista de pedidos</p>
    <tbody>
      <tr>
        <th>Item</th>
        <th>Quantidade</th>
        <th>Preço</th>
      </tr>
      <order v-for="order in orders"
            v-bind:order="order"
            v-bind:key="order.id" />
    </tbody>
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
p {
  width: 100%;
  font-size: 2em;
  color: blue;
}
th {
  width:45%;
}
</style>
