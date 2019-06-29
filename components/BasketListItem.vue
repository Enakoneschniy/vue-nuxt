<template>
  <li>
    {{ product.title }}, price: {{product.price}}
    <button @click="onDecrease(product.id)">-</button>
    <input type="text" :value="product.count" disabled>
    <button @click="onIncrease(product.id)">+</button>
    Total: {{totalPrice}}
    <button @click="onRemove(product.id)">Remove</button>
  </li>
</template>

<script>
  import { mapActions } from 'vuex';

  export default {
    name: "BasketListItem",
    props: {
      product: {
        type: Object,
        required: true
      }
    },
    computed: {
      totalPrice() {
        return this.product.price * this.product.count;
      }
    },
    methods: mapActions({
      onDecrease: 'Cart/DecreaseCount',
      onIncrease: 'Cart/IncreaseCount',
      onRemove: 'Cart/removeFromCart'
    })
  }
</script>

<style scoped>

</style>
