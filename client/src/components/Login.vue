<template>
  <v-layout column>
    <v-flex sm6 offset-sm3>
      <div>
        <v-toolbar flat dense color="grey darken-4">
          <v-toolbar-title>
            Login
          </v-toolbar-title>
        </v-toolbar>

        <div class="pl-4 pr-4 pt-2 pb-2">
          <v-text-field type="email" label="Email" v-model="email" color="teal lighten-4"></v-text-field>
          <br>
          <v-text-field type="password" label="Password" v-model="password" color="teal lighten-4"></v-text-field>
          <br>
          <div class="error" v-html="error"/>
          <br>
          <v-btn color="teal lighten-2" type="button" @click="login" light>
            Login
          </v-btn>
        </div>
      </div>
    </v-flex>
  </v-layout>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async login () {
      try {
        await AuthenticationService.login({
          email: this.email,
          password: this.password
        })
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  }
}
</script>

<style scoped>
  .error {
    padding: 0 5px;
    color: black;
  }

</style>
