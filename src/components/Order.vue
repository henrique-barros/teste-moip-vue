<template>
  <tr>
    <td>{{order.name}}</td>
    <td>{{order.amount}}</td>
    <td>{{getFormattedPrice(order.price)}}</td>
  </tr>
</template>

<script>
import Order from './Order'

export default {
  name: 'order',
  props: ['order'],
  methods: {
    getFormattedPrice: function(price) {
      let priceInReal = price/100;
      priceInReal = 'R$ ' + priceInReal.toFixed(2).toString().replace('.', ',');
      return priceInReal;
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
