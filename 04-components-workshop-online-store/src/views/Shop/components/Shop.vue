<script>
import Filters from './Filters.vue';
import ProductCard from './ProductCard.vue';
import {products} from '../../../constants/products.js';

export default {
    data() {
        return {
            selectedFilter: '',
            products
        }
    },
    computed:{
        displayProducts() {
            if (this.selectedFilter === '') 
                return this.products;

            return this.products.filter(product => product.category === this.selectedFilter)
        }
    },
    methods:{
        onFilterSelect(selected) {
            this.selectedFilter = selected;
        }
    },
    components: { Filters, ProductCard }
};
</script>

<template>
    <Filters :activeItem="selectedFilter" @on-select="onFilterSelect"/>
    <div class="products">
        <ProductCard v-for="product in displayProducts" :key="`products-${product.id}`" :product="product"/>
    </div>
</template>

<style scoped>
nav {
  padding: 0.25rem 1rem;
}

nav img {
  height: 2rem;
}

.products {
  display: grid;
  grid-template-columns: repeat(5, 1fr);
  gap: 1rem;
}

.footer {
  padding: 3em;
  background-color: #364954;
  color: white;
}

.footer * {
  color: white;
}

.footer .columns {
  display: grid;
  grid-template-columns: repeat(4, minmax(50px, 1fr));
  gap: 2rem;
}

.footer .section-header {
  border-bottom: 3px solid var(--primary);
  margin: 1rem;
  color: white;
}

.footer span {
  background: var(--primary);
  color: white;
  font-size: 26px;
  border-radius: 6px 6px 0 0;
  padding: 3px 17px;
  margin: auto;
}

.footer section {
  width: 100%;
  margin: 0.5em auto;
  vertical-align: top;
  text-align: center;
}

.footer ul {
  padding-left: 16px;
}

.footer li {
  list-style: none;
  border-bottom: 1px solid #444444;
  padding-bottom: 6px;
}

.footer a {
  text-decoration: none;
  color: white;
}

.footer div:nth-child(2) section {
  display: inline-block;
  vertical-align: top;
}

.footer div:nth-child(2) section:nth-child(2) {

  text-align: right;
}

.footer div:nth-child(2) .social-icons a {
  font-size: 26px;
  margin: 0.3em;
  padding: 10px;
}

.footer .svg-inline--fa {
  overflow: visible;
  width: 1em;
  display: inline-block;
  font-size: inherit;
  height: 1em;
  vertical-align: -0.125em;
}
</style>
