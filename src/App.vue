<template>
  <div class="wrapper">
    <header>
      <app-settings />
    </header>
    <product-list />
  </div>
</template>

<script>
import AppSettings from './components/AppSettings.vue';
import ProductList from './components/ProductList.vue';
export default {
  name: 'App',
  components: {
    ProductList,
    AppSettings
  }
}
</script>

<style lang="scss">
body {
  margin: 0;
  font-family: 'Roboto', sans-serif;
}

img {
  max-width: 100%;
}

.wrapper {
  margin: 0 auto;
  padding: 20px;
  max-width: 1100px;
}
</style>
