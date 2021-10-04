<template>
  <div class="ui card product">
    <div class="image">
      <img :src="API_URL + product.image.url" :alt="product.name" />
    </div>
    <div class="content">
      <div class="header">{{ product.name }}</div>
      <div class="description">{{ product.price }} $</div>
    </div>
    <div class="ui button primary" @click="addProductCart(product.id)">
      Comprar
    </div>
  </div>
</template>

<script>
import { API_URL } from '../utils/constants';
export default {
  name: 'Product',
  props: {
    product: Object,
  },
  setup(props) {
    console.log(props.product);

    return {
      API_URL,
    };
  },
};
</script>

<style></style>
