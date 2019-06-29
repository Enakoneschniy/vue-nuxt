<template>
  <div>
    <nuxt-link :to="{name: 'cart'}">Cart: ({{ count }})</nuxt-link>
  </div>
</template>

<script>
  import { mapGetters } from 'vuex'

  export default {
    name: "SmallBasket",
    computed: mapGetters({
      count: 'Cart/productsCount'
    })
  }
</script>

<style scoped>

</style>
