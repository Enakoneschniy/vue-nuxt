<template>
  <ul>
    <ProductListItem v-for="product of products" :key="product.id" :product="product"/>
  </ul>
</template>

<script>
  import { mapGetters } from 'vuex'
  import ProductListItem from "./ProductListItem";

  export default {
    name: "ProductList",
    components: { ProductListItem },
    computed: mapGetters({
      products: 'Products/products'
    })
  }
</script>

<style scoped>

</style>
