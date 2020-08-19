<template>
  <v-container class="fill-height" fluid>
    <v-row align="center" justify="center">
      <v-col cols="12" sm="8" md="4">
        <v-card class="elevation-12">
          <v-toolbar color="primary" dark flat>
            <v-toolbar-title>Login form</v-toolbar-title>
          </v-toolbar>
          <v-card-text>
            <form @submit.prevent="submit">
              <v-text-field
                v-model="login"
                label="Login"
                name="login"
                prepend-icon="mdi-account"
                type="text"
                :error-messages="loginErrors"
                required
                @input="$v.login.$touch()"
                @blur="$v.login.$touch()"
              ></v-text-field>

              <v-text-field
                id="password"
                v-model="password"
                label="Password"
                name="password"
                prepend-icon="mdi-lock"
                type="password"
                :error-messages="passwordErrors"
                required
                @input="$v.password.$touch()"
                @blur="$v.password.$touch()"
              ></v-text-field>
            </form>
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn color="primary" @click="submit">Login</v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import { validationMixin } from 'vuelidate'
import { required } from 'vuelidate/lib/validators'

export default {
  mixins: [validationMixin],
  validations: {
    login: { required },
    password: { required },
  },
  data: () => ({
    login: '',
    password: '',
  }),
  computed: {
    loginErrors() {
      const errors = []
      if (!this.$v.login.$dirty) return errors
      !this.$v.login.required && errors.push('Login is required.')

      return errors
    },
    passwordErrors() {
      const errors = []
      if (!this.$v.password.$dirty) return errors
      !this.$v.password.required && errors.push('Password is required.')

      return errors
    },
  },
  methods: {
    submit() {
      this.$v.$touch()

      if (this.$v.$invalid) return

      const user = {
        id: new Date().getTime(),
        name: 'Vasya Ivanov',
        login: this.login,
        avatar: '/1.png',
        email: 'test@test.ru',
      }
      this.$emit('login', user)
    },
  },
}
</script>
