<template>
  <div>
    <table class="table">
      <thead>
        <tr>
          <th>Manufacturers</th>
          <th></th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="manufacturer in manufacturers" :key="manufacturer._id">
          <td>{{manufacturer.name}}</td>
          <td class="modify"><router-link :to="'/admin/manufacturers/edit/' + manufacturer._id">Change</router-link></td>
          <td class="remove"><a @click="removeManufacturer(manufacturer._id)" href="#">Delete</a></td>
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
    if (this.manufacturers.length === 0) {
      this.$store.dispatch('allManufacturers');
    }
  },
  computed: {
    manufacturers() {
      return this.$store.getters.allManufacturers
    }
  },
  methods: {
    removeManufacturer(manufacturerId) {

      const res = confirm('Do you want to delete this Manufacturer？');

      if (res) {
        this.$store.dispatch('removeManufacturer', {
          manufacturerId,
        })
      }
    }
  }
}
</script>