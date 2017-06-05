<template>
  <container class="app-container">
    <grid :rwd="{compact: 'stack'}">
      <grid-item size="1/2" :rwd="{compact: '0/1'}">
        <p>Lista de pedidos</p>
      </grid-item>
      <grid-item size="1/2" :rwd="{compact: '1/1'}">
        <p>teste</p>
      </grid-item>
    </grid>
    <grid flat>
      <grid-item size="1/12">
        <div v-on:click="sortByColumn('status')">Status</div>
        <i v-if="sortBy=='status'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="3/12" v-on:click="sortByColumn('codigo')">
        <div v-on:click="sortByColumn('codigo')">Codigo</div>
        <i v-if="sortBy=='codigo'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="1/12" v-on:click="sortByColumn('meio')">
        <div v-on:click="sortByColumn('meio')">Meio</div>
        <i v-if="sortBy=='meio'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="1/12" v-on:click="sortByColumn('valor')">
        <div v-on:click="sortByColumn('valor')">R$</div>
        <i v-if="sortBy=='valor'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="3/12" v-on:click="sortByColumn('data_atualizado')">
        <div v-on:click="sortByColumn('data_atualizado')">Atualizado</div>
        <i v-if="sortBy=='data_atualizado'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="3/12" v-on:click="sortByColumn('cliente')">
        <div v-on:click="sortByColumn('cliente')">Cliente</div>
        <i v-if="sortBy=='cliente'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
    </grid>
    <order v-for="order in orders"
          v-bind:order="order"
          v-bind:key="order.id" />
  </container>
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
          status: "ok",
          codigo: "ABCD320391039",
          meio: "cartao",
          data_atualizado: new Date("October 13, 2014 11:13:00"),
          cliente: {
            nome: "Marcos",
            email: "marcos@uol.com"
          },
          valor: 800
        },
        {
          status: "ok",
          codigo: "EBCD320391030",
          meio: "dinheiro",
          data_atualizado: new Date("October 10, 2014 11:13:00"),
          cliente: {
            nome: "Henrique",
            email: "henrique@uol.com"
          },
          valor: 165
        },
        {
          status: "cancelado",
          codigo: "CBCD320391031",
          meio: "cartao",
          data_atualizado: new Date("October 15, 2014 11:13:00"),
          cliente: {
            nome: "Luciana",
            email: "lu@uol.com"
          },
          valor: 3284
        },
        {
          status: "ok",
          codigo: "DCCD320391039",
          meio: "cartao",
          data_atualizado: new Date("October 9, 2014 11:13:00"),
          cliente: {
            nome: "Maria Luiza",
            email: "maria@uol.com"
          },
          valor: 9323
        }
      ]
    }
  },
  methods: {
    sortByColumn: function(column) {
      console.log(column);
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
    isDateColumn: function(column) {
      return (typeof this.orders[0][column].getMonth === 'function')
    },
    isClienteColumn: function(column) {
      return (typeof this.orders[0][column].nome === 'string')
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
        else if (this.isDateColumn(column)) {
          this.orders.sort(function(a, b) {
            if (orderSort) {
              return a[column] - b[column];
            }
            return b[column] - a[column];
          })
        }
        else if (this.isClienteColumn(column)) {
          this.orders.sort(function(a, b) {
            if (orderSort) {
              return a[column]['nome'].localeCompare(b[column]['nome']);
            }
            return b[column]['nome'].localeCompare(a[column]['nome']);
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

.app-container {
  text-align: left;
}
</style>
