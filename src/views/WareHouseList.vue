<template>
  <div>
    <h1>Galpões Cadastrados</h1>

    <v-text-field label="Buscar Galpão" v-model="search" class="my-5"></v-text-field>
    
    <v-card>
      <v-card-text>
        <WarehouseTable :warehouses="filteredWareHouses" />
      </v-card-text>
    </v-card>
    
  </div>
</template>

<script>

import WarehouseTable from '../components/WarehouseTable.vue'

export default {
  name: 'WareHouseList',

  components: {
    WarehouseTable
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
