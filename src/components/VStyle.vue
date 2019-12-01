<script>
export default {
  name: 'v-style',
  render: function render(createElement) {
      return createElement('style', this.$slots["default"]);
    }
}
</script>