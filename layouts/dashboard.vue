<template>
  <v-app>
    <v-header></v-header>
    <NavigationDrawer :items="items" />
    <v-content>
      <v-toolbar flat color="background">
        <v-app-bar-nav-icon @click="toggleDrawer"></v-app-bar-nav-icon>
        <div class="headline ml-3 font-weight-bold" style="color: #555">
          Agrobank
        </div>
        <v-spacer></v-spacer>
        <v-btn class="logout" @click="logout" text>
          Logout
          <v-icon>mdi-login-variant</v-icon>
        </v-btn>
      </v-toolbar>
      <v-container class="mt-12" style="max-width: 80%">
        <nuxt />
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import NavigationDrawer from "~/components/NavigationDrawer";
import { eventBus } from "~/settings/settings";
export default {
  head() {
    return {
      title: "Dashboard"
    };
  },
  components: {
    NavigationDrawer
  },
  data() {
    return {
      id: this.$route.params.id,
      alert: {
        success: false,
        successMessage: "Success",
        error: false,
        errorMessage: "Error"
      }
    };
  },
  computed: {
    items() {
      return [
        {
          title: "Profile",
          icon: "mdi-view-dashboard",
          link: `/profile`
        },
        {
          title: "List of customers",
          icon: "mdi-format-list-bulleted",
          link: `/customers`
        },
        {
          title: "History of transactions",
          icon: "mdi-history",
          link: `/transactions`
        }
      ];
    }
  },
  methods: {
    toggleDrawer() {
      eventBus.$emit("toggle-nav-drawer");
    },
    logout() {
      this.$router.push({
        name: "index"
      })
    }
  }
};
</script>
