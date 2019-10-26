<template>
  <no-ssr>
    <v-container>
      <v-row>
        <v-col cols="12" sm="6" md="12">
          <v-breadcrumbs :items="items" large />
          <v-tabs>
            <v-tab>Cash In</v-tab>
            <v-tab>Profit-Centered</v-tab>
            <v-tab-item>
              <v-card
                class="mx-auto"
              >
                <v-card-text>
                  <v-row justify="end">
                    <v-dialog v-model="dialog" persistent max-width="600px">
                      <template v-slot:activator="{ on }">
                        <v-btn color="primary" dark v-on="on">
                          Open Dialog
                        </v-btn>
                      </template>
                      <v-card>
                        <v-card-title>
                          <span class="headline">User Profile</span>
                        </v-card-title>
                        <v-card-text>
                          <v-container>
                            <v-row>
                              <v-col cols="12">
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
                              </v-col>
                              <v-col cols="12">
                                <v-text-field label="Email*" required />
                              </v-col>
                              <v-col cols="12">
                                <v-text-field label="Password*" type="password" required />
                              </v-col>
                              <v-col cols="12" sm="6">
                                <v-select
                                  :items="['0-17', '18-29', '30-54', '54+']"
                                  label="Age*"
                                  required
                                />
                              </v-col>
                              <v-col cols="12" sm="6">
                                <v-autocomplete
                                  :items="['Skiing', 'Ice hockey', 'Soccer', 'Basketball', 'Hockey', 'Reading', 'Writing', 'Coding', 'Basejump']"
                                  label="Interests"
                                  multiple
                                />
                              </v-col>
                            </v-row>
                          </v-container>
                          <small>*indicates required field</small>
                        </v-card-text>
                        <v-card-actions>
                          <v-spacer />
                          <v-btn color="blue darken-1" text @click="dialog = false">
                            Close
                          </v-btn>
                          <v-btn color="blue darken-1" text @click="dialog = false">
                            Save
                          </v-btn>
                        </v-card-actions>
                      </v-card>
                    </v-dialog>
                  </v-row>
                </v-card-text>
                <v-card-text>
                  <ChartBar />
                </v-card-text>
                <v-row>
                  <v-col cols="12" sm="6" md="6">
                    <v-card
                      class="mx-auto"
                      outlined
                    >
                      <v-card-title>
                        Nutrition
                        <v-spacer />
                      </v-card-title>
                      <v-data-table
                        :headers="headers"
                        :items="desserts"
                        :items-per-page="5"
                        class="elevation-1"
                      />
                    </v-card>
                  </v-col>
                  <v-col cols="12" sm="6" md="6">
                    <v-card
                      class="mx-auto"
                      outlined
                    >
                      <v-card-title>
                        Nutrition
                        <v-spacer />
                      </v-card-title>
                      <v-data-table
                        :headers="headers"
                        :items="desserts"
                        :items-per-page="5"
                        class="elevation-1"
                      />
                    </v-card>
                  </v-col>
                </v-row>
              </v-card>
            </v-tab-item>
            <v-tab-item>
              <v-row>
                <v-col cols="12" sm="6" md="12">
                  <v-card
                    class="mx-auto"
                  >
                    <v-card-title>
                      Nutrition
                      <v-spacer />
                    </v-card-title>
                    <v-progress-linear
                      v-model="knowledge"
                      height="25"
                      reactive
                    >
                      <strong>{{ Math.ceil(knowledge) }}%</strong>
                    </v-progress-linear>
                  </v-card>
                </v-col>
              </v-row>
              <v-row>
                <v-col cols="12" sm="6" md="6">
                  <v-card
                    class="mx-auto"
                  >
                    <v-card-title>
                      Nutrition
                      <v-spacer />
                    </v-card-title>
                    <v-data-table
                      :headers="headers"
                      :items="desserts"
                      :items-per-page="5"
                      class="elevation-1"
                    />
                  </v-card>
                </v-col>
                <v-col cols="12" sm="6" md="6">
                  <v-card
                    class="mx-auto"
                  >
                    <v-card-title>
                      Nutrition
                      <v-spacer />
                    </v-card-title>
                    <v-data-table
                      :headers="headers"
                      :items="desserts"
                      :items-per-page="5"
                      class="elevation-1"
                    />
                  </v-card>
                </v-col>
              </v-row>
            </v-tab-item>
          </v-tabs>
        </v-col>
      </v-row>
    </v-container>
  </no-ssr>
</template>

<script>
import ChartBar from '@/components/chart-bar'
export default {
  components: {
    ChartBar
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
  },
  dialog: false,
  skill: 20,
  knowledge: 33,
  power: 78,
  headers: [
    {
      text: 'Dessert (100g serving)',
      align: 'left',
      sortable: false,
      value: 'name'
    },
    {
      text: 'Calories',
      value: 'calories'
    },
    {
      text: 'Fat (g)',
      value: 'fat'
    },
    {
      text: 'Carbs (g)',
      value: 'carbs'
    },
    {
      text: 'Protein (g)',
      value: 'protein'
    },
    {
      text: 'Iron (%)',
      value: 'iron'
    }
  ],
  desserts: [
    {
      name: 'Frozen Yogurt',
      calories: 159,
      fat: 6.0,
      carbs: 24,
      protein: 4.0,
      iron: '1%'
    },
    {
      name: 'Ice cream sandwich',
      calories: 237,
      fat: 9.0,
      carbs: 37,
      protein: 4.3,
      iron: '1%'
    },
    {
      name: 'Eclair',
      calories: 262,
      fat: 16.0,
      carbs: 23,
      protein: 6.0,
      iron: '7%'
    },
    {
      name: 'Cupcake',
      calories: 305,
      fat: 3.7,
      carbs: 67,
      protein: 4.3,
      iron: '8%'
    },
    {
      name: 'Gingerbread',
      calories: 356,
      fat: 16.0,
      carbs: 49,
      protein: 3.9,
      iron: '16%'
    },
    {
      name: 'Jelly bean',
      calories: 375,
      fat: 0.0,
      carbs: 94,
      protein: 0.0,
      iron: '0%'
    },
    {
      name: 'Lollipop',
      calories: 392,
      fat: 0.2,
      carbs: 98,
      protein: 0,
      iron: '2%'
    },
    {
      name: 'Honeycomb',
      calories: 408,
      fat: 3.2,
      carbs: 87,
      protein: 6.5,
      iron: '45%'
    },
    {
      name: 'Donut',
      calories: 452,
      fat: 25.0,
      carbs: 51,
      protein: 4.9,
      iron: '22%'
    },
    {
      name: 'KitKat',
      calories: 518,
      fat: 26.0,
      carbs: 65,
      protein: 7,
      iron: '6%'
    }
  ],
  items: [
    {
      text: 'Dashboard',
      disabled: false,
      href: 'breadcrumbs_dashboard'
    },
    {
      text: 'Link 1',
      disabled: false,
      href: 'breadcrumbs_link_1'
    },
    {
      text: 'Link 2',
      disabled: true,
      href: 'breadcrumbs_link_2'
    }
  ]
}
</script>

<style lang="scss" scoped>
.grid {
  display: grid;
  row-gap: 2rem;
}
</style>
