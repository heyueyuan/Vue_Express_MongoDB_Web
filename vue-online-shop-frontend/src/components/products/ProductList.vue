<template>
    <div>
        <div class="products">
            <div class="container">
                This is ProductList
            </div>
            <!-- <template v-for="product in products"> -->
            <product-item :product="product" :key="product._id"></product-item>
            <!-- </template> -->
        </div>
    </div>
</template>

<script>
import ProductItem from './ProductItem.vue';
export default {
    name: 'product-list',
    created() {
        // if (this.products.length === 0) {
        //     this.$store.dispatch('allProducts')
        // }
        return this.$store.state.products;
    },
    components: { 
        "product-item": ProductItem 
    },
    computed: {
        products() {
            return this.$store.getters.allProducts;
        }
    },
    // methods: {
    //     addToCart(product) {
    //         this.$store.commit('ADD_TO_CART', {
    //             product
    //         });
    //     }
    // }
}
</script>


<style>
.product {
  border-bottom: 1px solid black;
}

.product__image {
  width: 100px;
  height: 100px;
}
</style>