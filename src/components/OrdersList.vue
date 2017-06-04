<template>
  <div>
    <p>Lista de pedidos</p>
    <tbody>
      <tr>
        <th v-on:click="sortByColumn('name')">
          Item
          <i v-if="sortBy=='name'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
        </th>
        <th v-on:click="sortByColumn('amount')">
          Quantidade
          <i v-if="sortBy=='amount'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
        </th>
        <th v-on:click="sortByColumn('price')">
          Preço
          <i v-if="sortBy=='price'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
        </th>
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
      sortCrescent: true,
      sortBy: null,
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
      if (this.sortBy) {
        this.sortCrescent = !this.sortCrescent
      }
      this.sortBy = column;
      this.sortOrders()
    },
    hasOrders: function() {
      return this.orders && this.orders.length > 0;
    },
    isNumberColumn: function(column) {
      return (typeof this.orders[0][column] === 'number')
    },
    isStringColumn: function(column) {
      return (typeof this.orders[0][column] === 'string')
    },
    sortOrders: function() {
      const column = this.sortBy
      const orderSort = this.sortCrescent
      if (this.hasOrders()) {
        if (this.isNumberColumn(column)) {
          this.orders.sort(function(a, b) {
            if (orderSort) {
              return a[column] - b[column]
            }
            return b[column] - a[column]
          })
        }
        else if (this.isStringColumn(column)) {
          this.orders.sort(function(a, b) {
            if (orderSort) {
              return a[column].localeCompare(b[column])
            }
            return b[column].localeCompare(a[column])
          })
        }
      }
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
  cursor: pointer;
}
th:nth-child(1), th:nth-child(3) {
  width:30%;
}
th:nth-child(2) {
  width:40%;
}
i {
  margin-left: 4px;
}
</style>
