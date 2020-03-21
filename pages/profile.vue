<template>
  <div>
    <div class="display-1 text-center mb-5 font-weight-bold">
      Personal information
    </div>
    <v-card>
      <v-card-title>Personal data</v-card-title>
      <v-form
        ref="form"
        v-model="validForm"
        enctype="multipart/form-data"
      >
        <v-row>
          <v-col class="px-12">
            <v-text-field
              v-model="formData.email"
              label="Email"
              color="primary"
              required
              :rules="rules.email"
            >
            </v-text-field>
            <v-text-field
              v-model="formData.first_name"
              label="First name"
              color="primary"
              required
              :rules="rules.common"
            >
            </v-text-field>
            <v-text-field
              v-model="formData.middle_name"
              label="Middle name"
              :rules="rules.common"
              color="primary"
              required
            ></v-text-field>
            <v-text-field
              v-model="formData.last_name"
              label="Last name"
              color="primary"
              required
              :rules="rules.common"
            >
            </v-text-field>
          </v-col>
          <v-col class="px-12">
            
            
            <v-text-field
              v-model="formData.phone"
              :rules="rules.phone"
              label="Phone"
              color="primary"
            >
            </v-text-field>
                <v-text-field
                    v-model="formData.old_password"
                    :rules="rules.common"
                    type="password"
                    label="Old password"
                    required
                  ></v-text-field>
                  <v-text-field
                    v-model="formData.new_password"
                    label="New password"
                    :rules="rules.password"
                    type="password"
                    required
                  ></v-text-field>
                  <v-text-field
                    v-model="matchPassword"
                    label="Confirm password"
                    :rules="rules.match_password"
                    required
                    type="password"
                  ></v-text-field>
          </v-col>
        </v-row>
        <div class="button-container">
          <v-btn
            tile
            class="mb-5"
            color="primary"
            :disabled="!canSave"
            @click="save"
            >Save</v-btn
          >
        </div>
      </v-form>
    </v-card>
  </div>
</template>

<script>
import { mapState } from "vuex";
import { eventBus } from "~/settings/settings";
// import as from "~/services/AuthService";
// import es from "~/services/EmployerService";
export default {
  layout: "dashboard",
  head() {
    return {
      title: "Profile"
    };
  },
  data() {
    return {
      formData: {
          email: 'Anonymous@gmail.com',
          first_name: 'Anonim',
          middle_name: 'Batuevich',
          last_name: 'Manjaro',
          phone: '+99999999999',
          old_password: "",
          new_password: ""
      },
      matchPassword: "",
      id: this.$route.params.id,
      validForm: false,
      passForm: false,
      rules: {
        common: [v => !!v || "This field is required"],
        email: [
          v => !!v || "E-mail is required",
          v => /.+@.+\..+/.test(v) || "E-mail must be valid"
        ],
        checkbox: [v => !!v || "You must agree to continue!"],
        number: [v => !!v || "Please, specify a valid number"],
        password: [
          v => v.length > 8 || "Password should contain more that 8 symbols"
        ],
        match_password: [
          v =>
            v == this.formData.new_password ||
            "Passwords do not match!",
          v => !!v || "This field is required"
        ]
      },
      passwordFormData: {
        old_password: "",
        new_password: ""
      },
      matchPassword: "",
      passwordDialog: false
    };
  },
  computed: {
    canSave() {
      if (!this.validForm) {
        return false;
      }
      return true;
    }
  },
  methods: {
    save() {
        // pass
    },
  }
};
</script>

<style lang="scss">
.button-container {
    width: 100%;
    text-align: center;
}
</style>
