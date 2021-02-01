<template>
  <li class="catalog__item">
    <a class="catalog__pic" href="#" @click.prevent="gotoPage('product', { id: product.id })">
      <img :src="product.image" :alt="product.title" />
    </a>
    <h3 class="catalog__title">
      <a href="#">{{ product.title }}</a>
    </h3>
    <span class="catalog__price"> {{ product.price | numberFormat }} ₽ </span>

    <ProductColors class="product-page__colors" :colors="product.colors" :current-color.sync="productCurrentColor" />
  </li>
</template>
<style>
.product-page__colors .colors__value:hover {
  border: 1px solid #fff;
}
.product-page__colors .colors__value:hover::before {
  content: '';
  border: 1px solid #000;
}
</style>
<script>
import gotoPage from '@/helpers/gotoPage';
import numberFormat from '@/helpers/numberFormat';
import ProductColors from './ProductColors.vue';

export default {
  name: 'ProductItem',
  data() {
    return {
      productCurrentColor: this.product.colors[0].code,
    };
  },
  props: ['product', 'currentColor'],
  filters: {
    numberFormat,
  },
  components: {
    ProductColors,
  },
  methods: {
    gotoPage,
  },
};
</script>
