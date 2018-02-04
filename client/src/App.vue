<template>
  <div id="app">
    <v-app dark>
      <page-header/>
      <v-content>
        <v-container fluid>
          <router-view/>
        </v-container>
      </v-content>
    </v-app>
  </div>
</template>

<script>
import PageHeader from '@/components/Header.vue'

export default {
  name: 'App',
  components: {
    PageHeader
  }
}
</script>

<style>
#app {
  padding-top: 48px;
}

.danger-alert {
  color: red;
}
</style>
