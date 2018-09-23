<template>
  <v-container fluid>
    <v-layout align-center justify-center>
      <v-flex xs12 sm8>
        <v-card>
          <v-toolbar dark color="primary">
            <v-toolbar-title class="white--text">Login form</v-toolbar-title>
          </v-toolbar>
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-card-text>
              <v-text-field prepend-icon="person" v-model="email" label="E-Mail Address" type="email" :rules="[v => !!v || 'Email is required']" required></v-text-field>
              <v-text-field id="password" prepend-icon="lock" v-model="password" label="Password" type="password" :rules="[v => !!v || 'Password is required']" required></v-text-field>
            </v-card-text>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn flat :disabled="!valid" @click="onSubmit">{{ isLogin ? 'Login' : 'Sign Up' }}</v-btn>
              <v-btn flat @click="isLogin = !isLogin">Switch to {{ isLogin ? 'Signup' : 'Login' }}</v-btn>
            </v-card-actions>
          </v-form>
        </v-card>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
export default {
  data () {
    return {
      isLogin: true,
      valid: true,
      email: '',
      password: ''
    }
  },
  methods: {
    onSubmit () {
      if (this.$refs.form.validate()) {
        this.$store.dispatch('authenticateUser', {
          isLogin: this.isLogin,
          email: this.email,
          password: this.password
        })
          .then(() => {
            this.$router.push('/admin')
          })
      }
    }
  }
}
</script>
