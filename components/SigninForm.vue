<template>
  <v-app>
    <v-card
      width="400"
      class="mx-auto mt-10"
      style="transform: scale(1.2) !important; margin-top: 100px !important"
    >
      <v-card-title>
        <h1 class="display-2">
          Login
        </h1>
      </v-card-title>
      <v-card-text>
        <v-form v-model="validForm">
          <v-text-field
            v-model="credentials.username"
            label="Username"
            prepend-icon="mdi-account-circle"
            :rules="rules.username"
          />
          <v-text-field
            v-model="credentials.password"
            :type="showPassword ? 'text' : 'password' "
            label="Password"
            prepend-icon="mdi-lock"
            :rules="rules.password"
            :append-icon="showPassword ? 'mdi-eye' : 'mdi-eye-off'"
            @click:append="showPassword = !showPassword"
          />
          <v-card-actions>
            <v-btn color="success" @click="signin" :disabled="!canSignin">
              Login
            </v-btn>
          </v-card-actions>
        </v-form>
      </v-card-text>
    </v-card>
  </v-app>
</template>

<script>
import { eventBus } from '~/settings/settings'

export default {
  data () {
    return {
      showPassword: false,
      credentials: {
        username: '',
        password: ''
      },
      rules: {
          username: [
          v => !!v || "Username can't be empty",
        ],
          password: [
              v => !!v || "Password can't be empty",
              v => v.length > 8 || "Password should contain more than 8 symbols"
          ]
      },
      validForm: false
    }
  },
  created () {
    eventBus.$on('loading', (data) => {
      this.$nuxt.$loading.finish()
    })
  },
  computed: {
      canSignin() {
          if (!this.validForm) {
              return false;
          }
          
          return true;
      }
  },
  methods: {
    signin () {
      this.$nuxt.$loading.start()
      this.$router.push({
          name: "profile"
      })
    }
  }
}
</script>
