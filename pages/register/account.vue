<template>
  <v-container class="fill-height ma-0" fluid>
    <v-row justify="center">
      <v-col cols="12" sm="10" md="8" lg="6">
        <v-card-content class="pa-md-4 mx-lg-auto">
          <v-stepper value="1">
            <v-stepper-header>
              <v-stepper-step step="1">
                Profile
              </v-stepper-step>
              <v-divider />
              <v-stepper-step step="2">
                Business
                <!-- <small>Optional</small> -->
              </v-stepper-step>
              <v-divider />
              <v-stepper-step step="3">
                Category
              </v-stepper-step>
            </v-stepper-header>
          </v-stepper>
        </v-card-content>
        <v-card ref="form">
          <!-- <v-card-title>Sign Up</v-card-title> -->
          <v-card-text>
            <v-text-field
              ref="email"
              v-model="email"
              :rules="[() => !!email || 'This field is required']"
              :error-messages="errorMessages"
              label="Email"
              placeholder="example123@moneyking.com"
              required
            />
            <v-text-field
              v-model="password"
              :append-icon="show1 ? 'mdi-eye-off' : 'mdi-eye'"
              :rules="[rules.required, rules.min]"
              :type="show1 ? 'text' : 'password'"
              name="input-10-1"
              label="Password"
              hint="At least 8 characters"
              counter
              @click:append="show1 = !show1"
            />
            <v-text-field
              v-model="password"
              :append-icon="show1 ? 'mdi-eye-off' : 'mdi-eye'"
              :rules="[rules.required, rules.min]"
              :type="show1 ? 'text' : 'password'"
              name="input-10-1"
              label="Rewrite Password"
              hint="At least 8 characters"
              counter
              @click:append="show1 = !show1"
            />
            <v-checkbox
              v-model="checkbox"
              v-validate="'required'"
              value="1"
              label="I agree to Money King's terms"
              data-vv-name="checkbox"
              type="checkbox"
              required
            />
          </v-card-text>
          <!-- <v-divider class="mt-12"></v-divider> -->
          <v-card-actions>
            <!-- <v-btn text>Cancel</v-btn> -->
            <v-spacer />
            <v-slide-x-reverse-transition>
              <v-tooltip
                v-if="formHasErrors"
                left
              >
                <template v-slot:activator="{ on }">
                  <v-btn
                    icon
                    class="my-0"
                    v-on="on"
                  >
                    <v-icon>mdi-refresh</v-icon>
                  </v-btn>
                </template>
                <span>Refresh form</span>
              </v-tooltip>
            </v-slide-x-reverse-transition>
            <v-btn color="primary" text @click="submit">
              Submit
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  layout: 'empty',
  head () {
    return {
      title: 'Sign Up'
    }
  },
  data () {
    return {
      show1: false,
      password: 'Password',
      rules: {
        required: value => !!value || 'Required.',
        min: v => v.length >= 8 || 'Min 8 characters',
        emailMatch: () => ('The email and password you entered don\'t match')
      }
    }
  }
}
</script>

<style scoped>

</style>
