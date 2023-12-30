<template>
  <div>
    <h1>Galpões Cadastrados</h1>

    <input class="form" type="text" placeholder="Buscar Galpão" v-model="search" />

    <div v-for="w in filteredWareHouses" :key="w.id">
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
      warehouses: [],
      search: ''
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
  },

  computed: {
    filteredWareHouses() {
      return this.warehouses.filter(warehouse => {
        return warehouse.name.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  }
}
</script>

<style>

  .form {
    margin-bottom: 20px;
  }

</style>