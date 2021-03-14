<template>
        <main class="content container">
    <div class="content__top content__top--catalog">
      <h1 class="content__title">
        Каталог
      </h1>
      <span class="content__info">
        152 товара
      </span>
    </div>

    <div class="content__catalog">
      
      <ProductFilter :price-from.sync='filterPriceFrom' :price-to.sync='filterPriceTo' :category-id.sync='filterCategoryId'/>
      
      <section class="catalog">
        
        <ProductList :products='products'/>

        <BasePagination v-model='page' :count='countProducts' :perPage='productListPerPage'/>

      </section>

    </div>
  </main>
  
</template>

<script>
import products from '@/data/products'
import ProductList from '@/components/ProductList.vue'
import BasePagination from '@/components/BasePagination'
import ProductFilter from '@/components/ProductFilter'

export default {
  name: 'App',
  components: {ProductList, BasePagination, ProductFilter},
  data() {
    return {
      // products
      filterPriceFrom: 0,
      filterPriceTo: 0,
      filterCategoryId: 0,
      page: 1,
      productListPerPage: 3,
    }
  },
  computed: {
    filterProducts() {
      let filteredProducts = products;

      if(this.filterPriceFrom > 0) {
        filteredProducts = filteredProducts.filter(product => product.price > this.filterPriceFrom);
      }

      if(this.filterPriceTo > 0) {
        filteredProducts = filteredProducts.filter(product => product.price > this.filterPriceTo);
      }

      if(this.filterCategoryId) {
        filteredProducts = filteredProducts.filter(product => product.categoryId === this.filterCategoryId);
      }

      return filteredProducts
    },
    products() {
      const offset = (this.page - 1) * this.productListPerPage;
      return this.filterProducts.slice(offset, offset + this.productListPerPage)
    },
    countProducts() {
      return this.filterProducts.length
    }
  }
}
</script>


