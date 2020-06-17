<template>
  <div>
    <form v-if="!loggedin" id="login">
      <v-text-field
        v-model="user"
        type="text"
        autocomplete="username"
        label="user"
      />
      <v-text-field
        v-model="password"
        type="password"
        name="password"
        autocomplete="new-password"
        label="password"
      />
      <v-btn @click="login">login</v-btn>
      <v-btn @click="access">access password manager</v-btn>
    </form>
    <div v-else>
      logged in as <mark>{{ user }}</mark> with
      <mark>{{ password }}</mark>
      <v-btn @click="logout">logout</v-btn>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Credentials',
  data() {
    return {
      loggedin: false,
      user: '',
      password: ''
    }
  },
  methods: {
    async login() {
      if (this.user && this.password) {
        this.loggedin = true
        const credential = new window.PasswordCredential({
          id: this.user,
          password: this.password
        })
        console.log(credential)
        navigator.credentials.store(credential)
      }
    },
    logout() {
      this.loggedin = false
      this.user = this.password = ''
    },
    async access() {
      const credential = await navigator.credentials.get({ password: true })
      if (credential) {
        console.log(credential)
        this.user = credential.id
        this.password = credential.password
        this.$nextTick(() => this.login())
      }
    }
  }
}
</script>
