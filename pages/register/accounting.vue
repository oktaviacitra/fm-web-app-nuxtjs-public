<template>
  <v-container class="fill-height ma-0" fluid>
    <v-row justify="center">
      <v-col cols="12" sm="10" md="8" lg="6">
        <v-card-content class="pa-md-4 mx-lg-auto">
          <v-stepper value="3">
            <v-stepper-header>
              <v-stepper-step step="1" complete>
                Detail
              </v-stepper-step>
              <v-divider />
              <v-stepper-step step="2" complete>
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
              ref="capital"
              v-model="capital"
              :rules="[() => !!capital || 'This field is required']"
              :error-messages="errorMessages"
              label="Recent Capital"
              type="number"
              required
            />
            <v-text-field
              ref="cash"
              v-model="cash"
              :rules="[() => !!cash || 'This field is required']"
              :error-messages="errorMessages"
              label="Cash"
              type="number"
              required
            />
            <v-text-field
              ref="debt"
              v-model="debt"
              :rules="[() => !!debt || 'This field is required']"
              :error-messages="errorMessages"
              label="Debt"
              type="number"
              required
            />
            <v-text-field
              ref="expense"
              v-model="expense"
              :rules="[() => !!expense || 'This field is required']"
              :error-messages="errorMessages"
              label="Expense"
              type="number"
              required
            />
            <v-menu
              ref="menu1"
              v-model="menu1"
              :close-on-content-click="false"
              transition="scale-transition"
              offset-y
              full-width
              max-width="290px"
              min-width="290px"
            >
              <template v-slot:activator="{ on }">
                <v-text-field
                  v-model="dateFormatted"
                  label="Date"
                  hint="MM/DD/YYYY format"
                  persistent-hint
                  @blur="date = parseDate(dateFormatted)"
                  v-on="on"
                />
              </template>
              <v-date-picker v-model="date" no-title @input="menu1 = false" />
            </v-menu>
          </v-card-text>
          <!-- <v-divider class="mt-12"></v-divider> -->
          <v-card-actions>
            <v-btn text to="/register/type">
              Cancel
            </v-btn>
            <v-spacer />
            <v-btn color="primary" text to="/feature/dashboard/">
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
  data: vm => ({
    date: new Date().toISOString().substr(0, 10),
    dateFormatted: vm.formatDate(new Date().toISOString().substr(0, 10)),
    menu1: false
  }),

  computed: {
    computedDateFormatted () {
      return this.formatDate(this.date)
    }
  },

  watch: {
    date (val) {
      this.dateFormatted = this.formatDate(this.date)
    }
  },

  methods: {
    formatDate (date) {
      if (!date) { return null }

      const [year, month, day] = date.split('-')
      return `${month}/${day}/${year}`
    },
    parseDate (date) {
      if (!date) { return null }

      const [month, day, year] = date.split('/')
      return `${year}-${month.padStart(2, '0')}-${day.padStart(2, '0')}`
    }
  }
}
</script>
