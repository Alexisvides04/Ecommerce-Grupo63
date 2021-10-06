<template>
  <BasicLayouts>
    <h2>Estamos en la categoria</h2>
    {{ products }}
  </BasicLayouts>
</template>

<script>
import { ref, onMounted } from 'vue';
import { useRoute } from 'vue-router';
import BasicLayouts from '../layouts/BasicLayouts.vue';
import { getCategoriesApi, getProductsCategory } from '../api/product';

export default {
  name: 'Category',
  components: {
    BasicLayouts,
  },

  watch: {
    $route(to, from) {
      this.getProduts(to.params.category);
    },
  },

  setup() {
    let products = ref(null);
    const { params } = useRoute();

    onMounted(() => {
      getProduts(params.category);
    });

    const getProduts = async (categoty) => {
      const response = await getProductsCategory(categoty);
      products.value = response;
    };

    return {
      getProduts,
      products,
    };
  },
};
</script>
