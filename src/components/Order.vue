<template>
  <grid flat>
    <grid-item size="1/12">{{order.status}}</grid-item>
    <grid-item size="3/12">{{order.codigo}}</grid-item>
    <grid-item size="1/12">{{order.meio}}</grid-item>
    <grid-item size="1/12">{{getFormattedPrice(order.valor)}}</grid-item>
    <grid-item size="3/12">{{order.data_atualizado.toLocaleString()}}</grid-item>
    <grid-item size="3/12">{{order.cliente}}</grid-item>
  </grid>
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
