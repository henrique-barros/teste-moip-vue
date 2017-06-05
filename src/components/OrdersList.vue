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
    <grid flat class="orders-grid-header">
      <grid-item size="1/12">
        <span v-on:click="sortByColumn('status')">Status</span>
        <i v-if="sortBy=='status'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="2/12" v-on:click="sortByColumn('codigo')">
        <span v-on:click="sortByColumn('id')">Codigo</span>
        <i v-if="sortBy=='id'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="2/12" v-on:click="sortByColumn('payments')">
        <span v-on:click="sortByColumn('payments')">Meio</span>
        <i v-if="sortBy=='payments'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="1/12" v-on:click="sortByColumn('valor')">
        <span v-on:click="sortByColumn('amount')">R$</span>
        <i v-if="sortBy=='amount'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="3/12" v-on:click="sortByColumn('date')">
        <span v-on:click="sortByColumn('date')">Atualizado</span>
        <i v-if="sortBy=='date'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
      </grid-item>
      <grid-item size="3/12" v-on:click="sortByColumn('customer')">
        <span v-on:click="sortByColumn('customer')">Cliente</span>
        <i v-if="sortBy=='customer'" class="material-icons">{{sortCrescent ? "keyboard_arrow_up" : "keyboard_arrow_down"}}</i>
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
          "id": "380561",
          "ownId": "sandbox_v2_1430950122",
          "externalId": "ORD-U052MFZ4M414",
          "status": "WAITING",
          "blocked": false,
          "amount": {
            "total": 4000,
            "addition": 0,
            "fees": 335,
            "deduction": 0,
            "otherReceivers": 0,
            "currency": "BRL"
          },
          "receivers": [
            {
              "type": "PRIMARY",
              "moipAccount": {
                "id": "MPA-CULBBYHD11"
              }
            }
          ],
          "customer": {
            "fullname": "jose silva",
            "email": "sandbox_v2_1430950122@email.com"
          },
          "items": [
            {
              "product": null
            }
          ],
          "payments": [
            {
              "installmentCount": 1,
              "fundingInstrument": {
                "method": "CREDIT_CARD",
                "institution": "VISA"
              }
            }
          ],
          "events": [
            {
              "type": "PAYMENT.AUTHORIZED",
              "createdAt": "2015-05-06T19:09:06Z"
            }
          ],
          "_links": {
            "self": {
              "href": "https://sandbox.moip.com.br/v2/orders/ORD-U052MFZ4M414"
            }
          },
          "createdAt": "2015-05-06T19:08:43Z",
          "updatedAt": "2015-05-06T19:08:48Z"
        },
        {
          "id": "380560",
          "ownId": "sandbox_v2_1430950121",
          "externalId": "ORD-8MFXXQTTPEJ4",
          "status": "PAID",
          "blocked": false,
          "amount": {
            "total": 30050,
            "addition": 0,
            "fees": 335,
            "deduction": 0,
            "otherReceivers": 0,
            "currency": "BRL"
          },
          "receivers": [
            {
              "type": "PRIMARY",
              "moipAccount": {
                "id": "MPA-CULBBYHD11"
              }
            }
          ],
          "customer": {
            "fullname": "jose silva",
            "email": "sandbox_v2_1430950121@email.com"
          },
          "items": [
            {
              "product": null
            }
          ],
          "payments": [
            {
              "installmentCount": 1,
              "fundingInstrument": {
                "method": "MONEY",
                "institution": "VISA"
              }
            }
          ],
          "events": [
            {
              "type": "PAYMENT.AUTHORIZED",
              "createdAt": "2015-05-06T19:09:06Z"
            }
          ],
          "_links": {
            "self": {
              "href": "https://sandbox.moip.com.br/v2/orders/ORD-8MFXXQTTPEJ4"
            }
          },
          "createdAt": "2015-05-06T19:08:41Z",
          "updatedAt": "2015-05-06T19:08:48Z"
        },
        {
          "id": "380456",
          "ownId": "sandbox_v2_1430942777",
          "externalId": "ORD-3XCFS4BTBO38",
          "status": "PAID",
          "blocked": false,
          "amount": {
            "total": 4000,
            "addition": 0,
            "fees": 335,
            "deduction": 0,
            "otherReceivers": 0,
            "currency": "BRL"
          },
          "receivers": [
            {
              "type": "PRIMARY",
              "moipAccount": {
                "id": "MPA-CULBBYHD11"
              }
            }
          ],
          "customer": {
            "fullname": "jose silva",
            "email": "sandbox_v2_1430942777@email.com"
          },
          "items": [
            {
              "product": null
            }
          ],
          "payments": [
            {
              "installmentCount": 1,
              "fundingInstrument": {
                "method": "CREDIT_CARD",
                "institution": "VISA"
              }
            }
          ],
          "events": [
            {
              "type": "PAYMENT.AUTHORIZED",
              "createdAt": "2015-05-06T17:06:53Z"
            }
          ],
          "_links": {
            "self": {
              "href": "https://sandbox.moip.com.br/v2/orders/ORD-3XCFS4BTBO38"
            }
          },
          "createdAt": "2015-05-06T17:06:23Z",
          "updatedAt": "2015-05-06T17:06:42Z"
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
        else if (column === 'date') {
          this.orders.sort(function(a, b) {
            if (orderSort) {
              return new Date(a.events[a.events.length - 1].createdAt) - new Date(b.events[b.events.length - 1].createdAt) ;
            }
            return new Date(b.events[b.events.length - 1].createdAt) - new Date(a.events[a.events.length - 1].createdAt) ;
          })
        }
        else if (column === 'customer') {
          this.orders.sort(function(a, b) {
            if (orderSort) {
              return a[column]['fullname'].localeCompare(b[column]['fullname']);
            }
            return b[column]['fullname'].localeCompare(a[column]['fullname']);
          })
        }
        else if (column === 'amount') {
          this.orders.sort(function(a, b) {
            if (orderSort) {
              return (a[column].total - a[column].fees) - (b[column].total - b[column].fees)
            }
            return (b[column].total - b[column].fees) - (a[column].total - a[column].fees)
          })
        }
        else if (column === 'payments') {
          this.orders.sort(function(a, b) {
            if (orderSort) {
              return a[column][a[column].length -1]['fundingInstrument'].method.localeCompare(b[column][b[column].length -1]['fundingInstrument'].method);
            }
            return b[column][b[column].length -1]['fundingInstrument'].method.localeCompare(a[column][a[column].length -1]['fundingInstrument'].method);
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


.orders-grid-header > * {
  margin: auto;
}
.orders-grid-header {
  margin-bottom: 18px;
  width: 100%;
  height: 50px;
  padding: 10px;
}

span {
  height: 24px;
  color: white;
}
</style>
