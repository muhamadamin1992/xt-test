<template>
  <div class="product-list">
    <product-item v-for="item in items"
      :key="item.id"
      :imgUrl="addNull(item.id)"
      :name="item.name"
      :anno="item.anno"
      :price="item.price"
      :currency="item.currency_id"
      :categoryId="item.category_id"
      :category="categories[item.category_id]"
      />
    <div v-if="loading">
      <load-spinner />
    </div>
    <div v-else>
    <load-more v-if="!completed" @load-more="getData" />
    </div>
  </div>
</template>

<script>
import ProductItem from './ProductItem.vue';
import LoadMore from './LoadMore.vue';
import LoadSpinner from './LoadSpinner.vue';
export default {
  name: 'product-list',
  components: {
    ProductItem,
    LoadMore,
    LoadSpinner
  },
  data: function () {
    return {
      items: [],
      categories: {},
      completed: false,
      loading: false,
      offset: 0,
      nulls: ['000', '00', '0', ''],
    }
  },

  methods: {
    async getData() {
      this.loading = true;
      const res = await fetch(` https://api.jstask.iac.tender.pro/products?lim=4&off=${this.offset}`);
      const data = await res.json();
      let categories = [];
      
      if (data.length < 4) {
        this.completed = true;
      } else if (data.length === 4) {
        data.length = 3;
      }

      data.forEach(el => {
        if (!this.categories[el.category_id]) {
          categories.push(el.category_id);
        }
      });

      if (categories.length) {
        categories = await fetch(`https://api.jstask.iac.tender.pro/cat?id=${categories.join(',')}`);
        categories = await categories.json();
        categories.forEach(({id, name}) => {
          this.categories[id] = name;
        });
      }

      this.items.push(...data);
      this.offset += data.length;
      this.loading = false;
    },
    addNull(id) {
      return `http://jstask.iac.tender.pro/photo/${this.nulls[id.toString().length - 1]}${id}.jpg`;
    }
  },
  mounted: function() {
    this.getData();
  },
}
</script>

<style lang="scss">
  .product-list {
    display: grid;
    grid-template-columns: repeat(auto-fill, minmax(270px, 1fr));
    grid-gap: 20px;
  }
</style>