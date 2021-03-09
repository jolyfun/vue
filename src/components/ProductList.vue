<template>
    <ul class="catalog__list">

      <ProductItem v-for="(product, index) in products" :key="index" :product='products'></ProductItem>

    </ul>
</template>

<script>
  import ProductItem from '@/ProductItem'

  export default {
    components: {ProductItem: ProductItem},
    props: ['products']
  }
</script>