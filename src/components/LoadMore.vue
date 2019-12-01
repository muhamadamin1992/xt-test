<template>
  <button class="load-more" @click="$emit('load-more')"><span class="fa fa-cloud-download"></span> Показать еще</button>
</template>

<script>
export default {
  name: 'load-more'
}
</script>

<style lang="scss">
  .load-more {
    border: 2px solid #0a91c6;
    padding: 15px;
    font-size: 1rem;
    background-color: #fff;
    color: #0a91c6;
    border-radius: 5px;
    cursor: pointer;

    &:hover {
      background-color: #0a91c6;
      color: #fff;
    }
  }
</style>