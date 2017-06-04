<template>
  <tr>
    <td>{{order.status}}</td>
    <td>{{order.codigo}}</td>
    <td>{{order.meio}}</td>
    <td>{{getFormattedPrice(order.valor)}}</td>
    <td>{{order.data_atualizado.toLocaleString()}}</td>
    <td>{{order.cliente}}</td>
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
