<template>
  <div class="product">
    <div class="product__top">
      <div class="product__category">
        <span :class="categoryIcon"></span>
        <a href="#">{{category}}</a></div>
      <div :class="priceClass">{{price}}</div>
    </div>
    <div class="custom-width product__img">
      <img :src="imgUrl" :alt="name">
    </div>
    <a class="product__name" href="#">{{name}}</a>
    <p class="product__content custom-height">{{anno}}</p>
  </div>
</template>

<script>
export default {
  name: 'product-item',
  props: ['imgUrl', 'name', 'anno', 'category', 'categoryId', 'currency', 'price'],
  computed: {
    categoryIcon() {
      return `fa fa-${this.categoryId}`
    },
    priceClass() {
      return `product__price ${this.currency}`;
    }
  }
}
</script>

<style lang="scss">
  .product {
    display: flex;
    border: 1px solid #ddd;
    padding: 15px;
    font-size: 13px;
    box-sizing: border-box;
    border-radius: 5px;
    flex-direction: column;

    a {
      text-decoration: none;

      &:hover {
        text-decoration: underline;
      }
    }

    &__top {
      display: flex;
      align-items: center;
      justify-content: space-between;
    }

    &__category {
      color: #75ad25;

      a {
        color: inherit;
      }
    }

    &__img {
      display: flex;
      margin: 10px auto;
      flex-grow: 1;
      justify-content: center;
      align-items: center;

      img {
        width: 100%;
      }
    }

    &__price {
      color: #ff5c5c;
      font-size: 14px;
      font-weight: 700;
    }

    &__name {
      font-size: 14px;
      color: #0a91c6;
    }

    &__content {
      position: relative;
      margin: 10px 0;
      color: #666;
      line-height: 14px;
      overflow: hidden;

      &::after {
        content: "";
        position: absolute;
        left: 0;
        top: 0;
        width: 100%;
        height: 100%;
        background: linear-gradient(0deg, #ffffff 0%, rgba(255, 255, 255, 0) 14px);
        pointer-events: none;
      }
    }
  }

  .rub::after {
    content: '\00A0\20BD';
  }

  .usd::before {
    content: '$\00A0';
  }
</style>