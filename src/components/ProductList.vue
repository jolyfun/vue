<template>
    <ul class="catalog__list">

      <ProductItem v-for="product in products" :key="product.id" :product='product'></ProductItem>

    </ul>
</template>

<script>
  import ProductItem from '@/components/ProductItem'

  export default {
    components: {ProductItem: ProductItem},
    props: ['products']
  }
</script>