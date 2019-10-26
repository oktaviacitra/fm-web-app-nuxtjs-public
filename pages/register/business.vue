<template>
  <v-container class="fill-height ma-0" fluid>
    <v-row justify="center">
      <v-col cols="12" sm="10" md="8" lg="6">
        <v-card-content class="pa-md-4 mx-lg-auto">
          <v-stepper value="2">
            <v-stepper-header>
              <v-stepper-step step="1" complete>
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
              ref="name"
              v-model="name"
              :rules="[() => !!name || 'This field is required']"
              :error-messages="errorMessages"
              label="Company Name"
              placeholder="PT. Money King Tbk"
              required
            />
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
              ref="phonenumber"
              v-model="phonenumber"
              :rules="[() => !!phonenumber || 'This field is required']"
              :error-messages="errorMessages"
              label="Phone Number"
              placeholder="+628172919273"
              required
            />
            <v-text-field
              ref="address"
              v-model="address"
              :rules="[() => !!address || 'This field is required']"
              :error-messages="errorMessages"
              label="Address"
              placeholder="Jl. Kembang Mayang No. 59"
              required
            />
            <v-text-field
              ref="balance"
              v-model="balance"
              :rules="[() => !!balance || 'This field is required']"
              :error-messages="errorMessages"
              label="Balance"
              placeholder="821028291021001"
              required
            />
          </v-card-text>
          <!-- <v-divider class="mt-12"></v-divider> -->
          <v-card-actions>
            <v-btn text>
              Cancel
            </v-btn>
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
  }
}
</script>
