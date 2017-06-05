<template>
  <grid class="orders-grid" flat>
    <grid-item size="1/12">{{order.status}}</grid-item>
    <grid-item size="2/12">{{order.id}}</grid-item>
    <grid-item size="2/12">{{order.payments[order.payments.length - 1].fundingInstrument.method}}</grid-item>
    <grid-item size="1/12">{{getFormattedPrice(order.amount)}}</grid-item>
    <grid-item size="3/12">{{order.events[order.events.length - 1].createdAt}}</grid-item>
    <grid-item size="3/12">{{order.customer.fullname}}</grid-item>
  </grid>
</template>

<script>
import Order from './Order'

export default {
  name: 'order',
  props: ['order'],
  methods: {
    getFormattedPrice: function(price) {
      let priceInReal = (price.total - price.fees)/100;
      priceInReal = 'R$ ' + priceInReal.toFixed(2).toString().replace('.', ',');
      return priceInReal;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.orders-grid > * {
  margin: auto;
}
.orders-grid {
  border-radius: 40px;
  margin-bottom: 18px;
  background: white;
  border: 1px solid white;
  width: 100%;
  height: 50px;
  padding: 10px;
}
</style>
