<template v-for="product in products">
<div>
    <div class="product">
    <router-link :to="'/detail/' + product._id" :key="product._id" class="product-link">
        <p class="product_name"> Name: {{product.name}}</p>
        <p class="product_description">Description: {{product.description}}</p>
        <p class="product_price">Price: {{product.price}}</p>
        <p class="product.manufacturer">Manufacturer:{{product.manufacturer.name}}</p>
        <img :src="product.image" alt="" class="product_image">
    </router-link>
    <product-button :product="product"></product-button>
    </div>
</div>
</template>

<script>
import ProductButton from './ProductButton';
export default {
  name: 'product-item',
  props: ['product'],
  components: {
    'product-button': ProductButton
  }
}
</script>
