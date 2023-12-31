<template>
  <v-app>
    <Menu/>

    <v-container class="text-center">
      <v-row>
        <v-col>
          <router-view/>
        </v-col>
      </v-row>
    </v-container>

  </v-app>
</template>

<script>

import Menu from './components/Menu.vue'

export default {
  name: 'App',
  components: {
    Menu
  }
};
</script>
