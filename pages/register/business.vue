<template>
  <v-container class="fill-height ma-0" fluid>
    <v-row justify="center">
      <v-col cols="12" sm="10" md="8" lg="6">
        <v-card-content class="pa-md-4 mx-lg-auto">
          <v-stepper value="1">
            <v-stepper-header>
              <v-stepper-step step="1">
                Detail
              </v-stepper-step>
              <v-divider />
              <v-stepper-step step="2">
                Category
                <!-- <small>Optional</small> -->
              </v-stepper-step>
              <v-divider />
              <v-stepper-step step="3">
                Accounting
              </v-stepper-step>
            </v-stepper-header>
          </v-stepper>
        </v-card-content>
        <v-card ref="form" class="pa-md-4 mx-lg-auto">
          <!-- <v-card-title>Sign Up</v-card-title> -->
          <v-card-text>
            <v-text-field
              ref="name"
              v-model="name"
              :rules="[() => !!name || 'This field is required']"
              :error-messages="errorMessages"
              label="Company Name"
              type="text"
              placeholder="PT. Money King Tbk"
              required
            />
            <v-text-field
              ref="email"
              v-model="email"
              :rules="[() => !!email || 'This field is required']"
              :error-messages="errorMessages"
              label="Email"
              type="text"
              placeholder="example123@moneyking.com"
              required
            />
            <v-text-field
              ref="phonenumber"
              v-model="phonenumber"
              :rules="[() => !!phonenumber || 'This field is required']"
              :error-messages="errorMessages"
              label="Phone Number"
              type="text"
              placeholder="028172919273"
              required
            />
            <v-text-field
              ref="address"
              v-model="address"
              :rules="[() => !!address || 'This field is required']"
              :error-messages="errorMessages"
              label="Address"
              type="text"
              placeholder="Jl. Kembang Mayang No. 59"
              required
            />
          </v-card-text>
          <!-- <v-divider class="mt-12"></v-divider> -->
          <v-card-actions>
            <v-spacer />
            <v-btn color="primary" text to="/register/type">
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
