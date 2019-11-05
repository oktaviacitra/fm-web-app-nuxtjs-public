<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-card ref="form" class="pa-md-4 mx-lg-auto">
          <v-card-title>New Invoice</v-card-title>
          <v-card-text>
            <v-row>
              <v-col cols="4">
                <v-text-field label="Client Name" />
                <v-text-field label="Client Address" />
                <v-text-field label="Client Email" />
              </v-col>
              <v-col cols="4" />
              <v-col cols="4">
                <v-text-field label="Invoice ID" />
                <div>
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
                        label="Invoice Date"
                        persistent-hint
                        @blur="date = parseDate(dateFormatted)"
                        v-on="on"
                      />
                    </template>
                    <v-date-picker v-model="date" no-title @input="menu1 = false" />
                  </v-menu>
                </div>
                <div>
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
                        label="Due Date"
                        persistent-hint
                        @blur="date = parseDate(dateFormatted)"
                        v-on="on"
                      />
                    </template>
                    <v-date-picker v-model="date" no-title @input="menu1 = false" />
                  </v-menu>
                </div>
                <v-text-field label="Terms" />
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="12">
                <DraftCRUD />
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="4">
                <v-textarea
                  label="Note"
                />
              </v-col>
              <v-col cols="4" />
              <v-col cols="4">
                <v-text-field label="Subtotal" />
                <v-text-field label="Discount" />
                <v-text-field label="Added Discount" />
                <v-text-field label="Total" />
              </v-col>
            </v-row>
          </v-card-text>
          <v-card-actions class="text-center">
            <v-spacer />
            <v-btn class="ma-2" outlined color="indigo" to="/feature/invoice/">
              Save as Draft
            </v-btn>
            <v-btn class="ma-2" tile color="indigo" dark to="/feature/invoice/sendto">
              Finish
            </v-btn>
            <v-spacer />
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
import DraftCRUD from '@/components/DraftCRUD'
export default {
  components: {
    DraftCRUD
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
