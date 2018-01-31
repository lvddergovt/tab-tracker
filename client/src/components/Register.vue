<template>
  <v-flex sm10 md6 offset-sm1 offset-md3>
    <panel title="Register">
      <form autocomplete="off">
        <v-text-field type="email" label="Email" v-model="email" color="teal lighten-4"></v-text-field>
        <br>
        <v-text-field type="password" label="Password" v-model="password" color="teal lighten-4"></v-text-field>
        <br>
        <div class="error" v-html="error"/>
        <br>
        <v-btn color="teal lighten-2" type="submit" @click="register" light>
          Register
        </v-btn>
      </form>
    </panel>
  </v-flex>
</template>

<script>
import AuthenticationService from '@/services/AuthenticationService'
import Panel from '@/components/Panel'
export default {
  data () {
    return {
      email: '',
      password: '',
      error: null
    }
  },
  methods: {
    async register () {
      try {
        const response = await AuthenticationService.register({
          email: this.email,
          password: this.password
        })
        this.$store.dispatch('setToken', response.data.token)
        this.$store.dispatch('setUser', response.data.user)
      } catch (error) {
        this.error = error.response.data.error
      }
    }
  },
  components: {
    Panel
  }
}
</script>

<style scoped>
  .error {
    padding: 0 5px;
    color: black;
  }

</style>
