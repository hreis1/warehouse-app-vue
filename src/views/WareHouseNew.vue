<template>
  <div>
    <h1>Cadastrar Galpão</h1>

    <div class="container">

      <v-alert v-if="msg" type="info">{{ msg }}</v-alert>           
      <v-form v-on:submit.prevent>

        <v-text-field  label="Código" v-model="form.code"></v-text-field>
        <v-text-field  label="Nome" v-model="form.name"></v-text-field>
        <v-text-field  label="Endereço" v-model="form.address"></v-text-field>
        <v-text-field  label="Cidade" v-model="form.city"></v-text-field>
        <v-text-field  label="CEP" v-model="form.cep"></v-text-field>
        <v-text-field  label="Área" v-model="form.area"></v-text-field>
        <v-textarea  label="Descrição" v-model="form.description"></v-textarea>

        <v-btn v-on:click="postWareHouse" color="primary">Cadastrar</v-btn>

      </v-form>
    </div>
  </div>
</template>

<script>
export default {
  name: 'WareHouseNew',
  
  data() {
    return {
      msg: null,
      form: {
        code: null,
        name: null,
        address: null,
        city: null,
        cep: null,
        area: null,
        description: null
      }
    }
  },

  methods: {
    async postWareHouse() {
      try{
        await this.$http.post('http://localhost:3000/api/v1/warehouses', {
          code: this.form.code,
          name: this.form.name,
          address: this.form.address,
          city: this.form.city,
          cep: this.form.cep,
          area: this.form.area,
          description: this.form.description
        })
        this.msg = 'Galpão cadastrado com sucesso!'
        return this.form = {}
      } catch (err) {
        this.msg = 'Erro ao cadastrar galpão!'
        return console.log(err)
      }
    }
  }
}
</script>

<style>
  .form {
    margin-bottom: 15px;
  }

  .form input {
    margin: 5px;
  }

</style>