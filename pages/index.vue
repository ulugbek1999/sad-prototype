<template>
  <v-app>
    <v-content>
      <signin-form />
    </v-content>
  </v-app>
</template>

<script>
import SigninForm from '~/components/SigninForm.vue'
import { eventBus } from '~/settings/settings'
export default {
  components: {
    'signin-form': SigninForm
  },
  created () {
    eventBus.$on('routed', (data) => {
      if (data) {
        this.$router.push({ name: 'index' })
      }
    })
  }
}
</script>