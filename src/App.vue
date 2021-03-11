<template>
 
      <section class="catalog">
        
        <ProductList :products='products'/>

        <BasePagination v-model='page' :count='countProducts' :perPage='productListPerPage'/>

      </section>
  
</template>

<script>
import products from '@/data/products'
import ProductList from '@/components/ProductList.vue'
import BasePagination from '@/components/BasePagination'

export default {
  name: 'App',
  components: {ProductList, BasePagination},
  data() {
    return {
      // products
      page: 1,
      productListPerPage: 3,
    }
  },
  computed: {
    products() {
      const offset = (this.page - 1) * this.productListPerPage;
      return products.slice(offset, offset + this.productListPerPage)
    },
    countProducts() {
      return products.length
    }
  }
}
</script>


