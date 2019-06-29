<template>
  <li>
    {{ product.title }}, price: {{product.price}} <button @click="onBuy(product)">Buy</button>
  </li>
</template>

<script>
  import { mapActions } from 'vuex'
  export default {
    name: "ProductListItem",
    props: {
      product: {
        type: Object,
        required: true
      }
    },
    methods: mapActions({
      onBuy: 'Cart/addToCart'
    })
  }
</script>

<style scoped>

</style>
