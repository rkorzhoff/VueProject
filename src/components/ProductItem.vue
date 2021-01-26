<template>
  <li class="catalog__item">
    <a class="catalog__pic" href="#">
      <img :src="product.image" :alt="product.title" />
    </a>
    <h3 class="catalog__title">
      <a href="#">{{ product.title }}</a>
    </h3>
    <span class="catalog__price"> {{ product.price }} ₽ </span>

    <ProductColors :colors="product.colors" :current-color.sync="productCurrentColor" />
  </li>
</template>

<script>
import ProductColors from './ProductColors.vue';

export default {
  name: 'ProductItem',
  data() {
    return {
      productCurrentColor: this.product.colors[0].code,
    };
  },
  props: ['product', 'currentColor'],
  components: {
    ProductColors,
  },
};
</script>
