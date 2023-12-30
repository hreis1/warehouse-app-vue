<template>
  <div>
    <h1>Galpões Cadastrados</h1>

    <div v-for="w in warehouses" :key="w.id">
      <WareHouse
        :id="w.id"
        :name="w.name"
        :address="w.address"
        :code="w.code"
        :city="w.city"
        :area="w.area"
      />
    </div>

  </div>

</template>

<script>

import WareHouse from '@/components/WareHouse.vue'

export default {
  name: 'WareHouseList',

  components: {
    WareHouse
  },

  data() {
    return {
      warehouses: []
    }
  },

  async mounted() {
    this.getWareHouses()
  },

  methods: {
    async getWareHouses() {
      const response = await this.$http.get('http://localhost:3000/api/v1/warehouses')
      const result = await response.json()
      this.warehouses = result
      return this.warehouses
    }
  }
}
</script>

<style>

</style>