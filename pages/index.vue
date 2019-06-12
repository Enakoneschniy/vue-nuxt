<template>
  <section class="container">
    <div>
      <logo/>
      <ul>
        <li>
          <nuxt-link :to="{name: 'tab-1'}">Tab 1</nuxt-link>
        </li>
        <li>
          <nuxt-link :to="{name: 'tab-2'}">Tab 2</nuxt-link>
        </li>
      </ul>
      <div class="child-container">
        <nuxt-child/>
      </div>
    </div>
  </section>
</template>

<script>
  import Logo from '../components/Logo.vue'

  export default {
    components: {
      Logo
    }
  }
</script>

<style scoped lang="sass">
  .child-container
    border: 1px solid gray
    width: 80%
    margin: 0 auto
    min-height: 200px
</style>
