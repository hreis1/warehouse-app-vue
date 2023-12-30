<template>
  <div>
    <h1>Cadastrar Galpão</h1>

    <div class="container">

      {{ msg }}
      
      <form v-on:submit.prevent>

        <div class="form">
          <label for="code">Código</label>
          <input type="text" id="code" v-model="form.code">
        </div>

        <div class="form">
          <label for="name">Nome</label>
          <input type="text" id="name" v-model="form.name">
        </div>

        <div class="form">
          <label for="address">Endereço</label>
          <input type="text" id="address" v-model="form.address">
        </div>

        <div class="form">
          <label for="city">Cidade</label>
          <input type="text" id="city" v-model="form.city">
        </div>

        <div class="form">
          <label for="cep">CEP</label>
          <input type="text" id="cep" v-model="form.cep">
        </div>

        <div class="form">
          <label for="area">Área</label>
          <input type="text" id="area" v-model="form.area">
        </div>

        <div class="form">
          <label for="description">Descrição</label>
          <textarea cols="30" rows="10" id="description" v-model="form.description"></textarea>
        </div>

        <div class="form">
          <button v-on:click="postWareHouse">Cadastrar</button>
        </div>

      </form>
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
      } catch (err) {
        this.msg = 'Erro ao cadastrar galpão!'
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