<template>
  <BasicLayouts>
    <h2>Estamos en Home</h2>
  </BasicLayouts>
</template>

<script>
import { ref, onMounted } from 'vue';
import BasicLayouts from '../layouts/BasicLayouts.vue';
import { getProducts } from '../api/product';

export default {
  name: 'Home',
  components: {
    BasicLayouts,
  },
  setup() {
    let products = ref(null);

    onMounted(async () => {
      const response = await getProducts(20);
      products.value = response;
    });
  },
};
</script>
