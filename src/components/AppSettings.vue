<template>
  <div class="settings">
    <label class="settings__label" for="setting-width">Максимальный размер изображения: {{customWidth}}x{{customWidth}}</label>
    <input class="settings__range" id="setting-width" v-model="customWidth" type="range" min="100" max="250" step="1">
    <label class="settings__label" for="setting-height">Минимальная высота описания: {{customHeight}} строк</label>
    <input class="settings__range" id="setting-height" v-model="customHeight" type="range" min="1" max="10" step="1">
    <v-style>
      .custom-width {
        width: {{customWidth}}px;
      }
      .custom-height {
        height: {{customHeight * 14}}px;
      }
    </v-style>
  </div>
</template>

<script>
import VStyle from './VStyle.vue';
export default {
  name: 'app-settings',
  components: {
    VStyle
  },
  data: function () {
    return {
      customWidth: 250,
      customHeight: 4
    }
  },
}
</script>
<style lang="scss">
  .settings {
    font-size: 13px;
    color: #333;

    &__label {
      display: block;
    }
  }
</style>