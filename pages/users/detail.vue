<template>
  <div class="container">
    <h1>One user</h1>
  </div>
</template>

<script>
  export default {
    name: "detail",
    scrollToTop: true,
    validate ({ params }) {
      // Must be a number
      return /^\d+$/.test(params.id)
    },
    async asyncData ({ params, query}) {
      console.log(params, query);
    }

  }
</script>

<style scoped>

</style>
