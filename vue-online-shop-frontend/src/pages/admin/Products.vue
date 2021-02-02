<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th>Name</th>
          <th>Price</th>
          <th>Manufacturer</th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="product in products" :key="product._id">
          <td>{{product.name}}</td>
          <td>{{product.price}}</td>
          <td>{{product.manufacturer.name}}</td>
          <td class="modify"><router-link :to="'/admin/edit/' + product._id">Change</router-link></td>
          <td class="remove"><a @click="removeProduct(product._id)" href="#">Delete</a></td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<style>
table {
  margin: 0 auto;
}

.modify {
  color: blue;
}

.remove a {
  color: red;
}
</style>

<script>
export default {
  created() {
    if (this.products.length === 0) {
      this.$store.dispatch('allProducts');
    }
  },
  computed: {
    products() {
      return this.$store.getters.allProducts
    }
  },
  methods: {
    removeProduct(productId) {
      const res = confirm('Do you want to delete this product?');


      if (res) {
        this.$store.dispatch('removeProduct', {
          productId,
        })
      }
    }
  }
}
</script>