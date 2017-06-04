<template>
  <div>
    <p>Lista de pedidos</p>
    <tbody>
      <tr>
        <th v-on:click="sortByColumn('name')">Item</th>
        <th v-on:click="sortByColumn('amount')">Quantidade</th>
        <th v-on:click="sortByColumn('price')">Preço</th>
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
          amount: 1,
          price: 800
        },
        {
          name: "Heineken",
          amount: 6,
          price: 3600
        },
        {
          name: "Toalha de banho",
          amount: 1,
          price: 1500
        },
        {
          name: "Caixa de fósforos",
          amount: 8,
          price: 500
        }
      ]
    }
  },
  methods: {
    sortByColumn: function(column) {
      if (this.hasOrders()) {
        if (this.isNumberColumn(column)) {
          this.orders.sort(function(a, b) {
            return a[column] - b[column]
          })
        }
        else if (this.isStringColumn(column)) {
          this.orders.sort(function(a, b) {
            return a[column].localeCompare(b[column])
          })
        }
      }
    },
    hasOrders: function() {
      return this.orders && this.orders.length > 0;
    },
    isNumberColumn: function(column) {
      return (typeof this.orders[0][column] === 'number')
    },
    isStringColumn: function(column) {
      return (typeof this.orders[0][column] === 'string')
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
