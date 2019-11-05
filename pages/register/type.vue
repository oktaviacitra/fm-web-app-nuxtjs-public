<template>
  <v-container class="fill-height ma-0" fluid>
    <v-row justify="center">
      <v-col cols="12" sm="10" md="8" lg="6">
        <v-card-content class="pa-md-4 mx-lg-auto">
          <v-stepper value="2">
            <v-stepper-header>
              <v-stepper-step step="1" complete>
                Detail
              </v-stepper-step>
              <v-divider />
              <v-stepper-step step="2">
                Category
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
            <v-select
              :items="items"
              label="Standard"
            />
            <v-text-field
              ref="others"
              v-model="Category"
              type="text"
              label="Others (optional)"
              placeholder="Etc."
              required
            />
          </v-card-text>
          <!-- <v-divider class="mt-12"></v-divider> -->
          <v-card-actions>
            <v-btn text to="/register/business">
              Cancel
            </v-btn>
            <v-spacer />
            <v-btn color="primary" text to="/register/accounting">
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
  data: () => ({
    items: ['Foo', 'Bar', 'Fizz', 'Buzz']
  })
}
</script>
