<template>
  <li class="catalog__item">
    <a class="catalog__pic" href="#">
      <img :src="product.image" :alt="product.title" />
    </a>

    <h3 class="catalog__title">
      <a href="#">{{ product.title }}</a>
    </h3>

    <span class="catalog__price">{{ product.price }}</span>

    <ul class="colors colors--black">
      <li class="colors__item" v-for="colorId in product" :key="colorId">
        <label class="colors__label">
          <input class="colors__radio sr-only" type="radio" :value="colorId" />
          <span class="colors__value" v-for="color in colors" :key="color" :style="color.color"> </span>
        </label>
      </li>
    </ul>
  </li>
</template>
<script>
import colors from '../data/colors';

export default {
  data() {
    return {
      productColor: 0,
    };
  },
  props: ['product'],

  computed: {
    colors() {
      return colors;
    },
  },
  watch: {
    product(color) {
      this.productColor = color;
    },
  },
};
</script>
