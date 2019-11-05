<template>
  <no-ssr>
    <v-container>
      <v-row>
        <v-col cols="12" sm="6" md="10" />
        <v-col cols="12" sm="6" md="2">
          <v-btn class="mx-2" fab dark color="indigo">
            <v-icon dark>
              mdi-plus
            </v-icon>
          </v-btn>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="6" md="3">
          <v-card
            class="mx-auto"
          >
            <v-card-text>
              <div class="text--primary">
                <div class="subtitle-1 font-weight-medium ">
                  Total Item
                </div>
                <div class="display-1 font-weight-bold text-right">
                  456
                </div>
              </div>
            </v-card-text>
            <v-divider />
            <v-card-actions>
              <div class="caption">
                <v-icon color="grey lighten-1">
                  mdi-calendar-clock
                </v-icon> Last 24 hours
              </div>
              <v-btn icon v-on="on">
                <v-icon color="grey lighten-1">
                  mdi-dots-horizontal
                </v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
        <v-col cols="12" sm="6" md="3">
          <v-card
            class="mx-auto"
          >
            <v-card-text>
              <div class="text--primary">
                <div class="subtitle-1 font-weight-medium ">
                  Total Category
                </div>
                <div class="display-1 font-weight-bold text-right">
                  62
                </div>
              </div>
            </v-card-text>
            <v-divider />
            <v-card-actions>
              <div class="caption">
                <v-icon color="grey lighten-1">
                  mdi-calendar-clock
                </v-icon> Last 24 hours
              </div>
              <v-btn icon v-on="on">
                <v-icon color="grey lighten-1">
                  mdi-dots-horizontal
                </v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
        <v-col cols="12" sm="6" md="3">
          <v-card
            class="mx-auto"
          >
            <v-card-text>
              <div class="text--primary">
                <div class="subtitle-1 font-weight-medium ">
                  Total Debt
                </div>
                <div class="display-1 font-weight-bold text-right">
                  Rp. 954.000
                </div>
              </div>
            </v-card-text>
            <v-divider />
            <v-card-actions>
              <div class="caption">
                <v-icon color="grey lighten-1">
                  mdi-calendar-clock
                </v-icon> Last 24 hours
              </div>
              <v-btn icon v-on="on">
                <v-icon color="grey lighten-1">
                  mdi-dots-horizontal
                </v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
        <v-col cols="12" sm="6" md="3">
          <v-card
            class="mx-auto"
          >
            <v-card-text>
              <div class="text--primary">
                <div class="subtitle-1 font-weight-medium ">
                  Growth
                </div>
                <div class="display-1 font-weight-bold text-right">
                  <v-icon color="green accent-4">
                    mdi-trending-up
                  </v-icon>40%
                </div>
              </div>
            </v-card-text>
            <v-divider />
            <v-card-actions>
              <div class="caption">
                <v-icon color="grey lighten-1">
                  mdi-calendar-clock
                </v-icon> Last 24 hours
              </div>
              <v-btn icon v-on="on">
                <v-icon color="grey lighten-1">
                  mdi-dots-horizontal
                </v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
      <v-row>
        <v-col cols="12" sm="6" md="9">
          <v-card
            class="mx-auto"
            outlined
          >
            <v-card-title>
              Products
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
        <v-col cols="12" sm="6" md="3">
          <v-card
            class="mx-auto"
            outlined
          >
            <v-card-title>
              Category
              <v-spacer />
            </v-card-title>
            <v-data-table
              :headers="headers"
              :items="desserts"
              :items-per-page="4"
              class="elevation-1"
            />
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </no-ssr>
</template>

<script>

export default {
  data () {
    return {
      skill: 20,
      knowledge: 33,
      power: 78,
      headers: [
        {
          text: 'Date',
          align: 'left',
          sortable: false,
          value: 'name'
        },
        { text: 'Account ID', value: 'calories' },
        { text: 'Type', value: 'fat' },
        { text: 'From', value: 'carbs' },
        { text: 'To', value: 'protein' },
        { text: 'Description', value: 'iron' },
        { text: 'Amount', value: 'amount' }
      ],
      desserts: [
        {
          name: 'Frozen Yogurt',
          calories: 159,
          fat: 6.0,
          carbs: 24,
          protein: 4.0,
          iron: '1%',
          amount: '5.000.0000'
        },
        {
          name: 'Ice cream sandwich',
          calories: 237,
          fat: 9.0,
          carbs: 37,
          protein: 4.3,
          iron: '1%',
          amount: '5.000.0000'
        },
        {
          name: 'Eclair',
          calories: 262,
          fat: 16.0,
          carbs: 23,
          protein: 6.0,
          iron: '7%',
          amount: '5.000.0000'
        },
        {
          name: 'Cupcake',
          calories: 305,
          fat: 3.7,
          carbs: 67,
          protein: 4.3,
          iron: '8%',
          amount: '5.000.0000'
        },
        {
          name: 'Gingerbread',
          calories: 356,
          fat: 16.0,
          carbs: 49,
          protein: 3.9,
          iron: '16%',
          amount: '5.000.0000'
        },
        {
          name: 'Jelly bean',
          calories: 375,
          fat: 0.0,
          carbs: 94,
          protein: 0.0,
          iron: '0%',
          amount: '5.000.0000'
        },
        {
          name: 'Lollipop',
          calories: 392,
          fat: 0.2,
          carbs: 98,
          protein: 0,
          iron: '2%',
          amount: '5.000.0000'
        },
        {
          name: 'Honeycomb',
          calories: 408,
          fat: 3.2,
          carbs: 87,
          protein: 6.5,
          iron: '45%',
          amount: '5.000.0000'
        },
        {
          name: 'Donut',
          calories: 452,
          fat: 25.0,
          carbs: 51,
          protein: 4.9,
          iron: '22%',
          amount: '5.000.0000'
        },
        {
          name: 'KitKat',
          calories: 518,
          fat: 26.0,
          carbs: 65,
          protein: 7,
          iron: '6%',
          amount: '5.000.0000'
        }
      ]
    }
  }
}
</script>

<style lang="scss" scoped>
.grid {
  display: grid;
  row-gap: 2rem;
}
</style>
