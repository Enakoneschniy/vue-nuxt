<template>
  <div class="header">
    <div class="container d-flex justify-content-between">
      <nuxt-link :to="{ name: 'home' }">Home</nuxt-link>
      <SmallBasket/>
    </div>

  </div>
</template>

<script>
  import SmallBasket from "./SmallBasket";
  export default {
    name: "MainHeader",
    components: { SmallBasket }
  }
</script>

<style scoped lang="sass">
.header
  padding: 10px
  border-bottom: 1px solid gray
  background: #F5F5F5
</style>
