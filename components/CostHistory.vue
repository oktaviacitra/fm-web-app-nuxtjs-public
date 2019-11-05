<template>
  <v-dialog v-model="dialog" width="600px">
    <template v-slot:activator="{ on }">
      <v-btn color="primary" dark v-on="on">
        History
      </v-btn>
    </template>
    <v-card>
      <v-card-title>
        <span class="headline">History</span>
      </v-card-title>
      <v-card-text>
        <v-data-table
          :headers="headers"
          :items="desserts"
          :items-per-page="5"
          class="elevation-1"
        />
      </v-card-text>
      <v-card-actions>
        <v-spacer />
        <v-btn color="green darken-1" text @click="dialog = false">
          Close
        </v-btn>
      </v-card-actions>
    </v-card>
  </v-dialog>
</template>
<script>
export default {
  data () {
    return {
      dialog: false,
      headers: [
        {
          text: 'ID',
          align: 'left',
          sortable: false,
          value: 'ID'
        },
        { text: 'Title', value: 'title' },
        { text: 'Period', value: 'period' },
        { text: 'Target', value: 'target' },
        { text: 'Percent', value: 'percent' }
      ],
      desserts: [
        {
          ID: 'Y101',
          title: 'Minimum Cost in July',
          period: '1 Month',
          target: '6.000.000',
          percent: '70%'
        },
        {
          ID: 'Y102',
          title: 'Minimum Cost in August',
          period: '1 Month',
          target: '5.000.000',
          percent: '60%'
        },
        {
          ID: 'Y103',
          title: 'Minimum Cost in September',
          period: '1 Month',
          target: '5.500.000',
          percent: '65%'
        },
        {
          ID: 'Y104',
          title: 'Minimum Cost in October',
          period: '1 Month',
          target: '6.000.000',
          percent: '50%'
        },
        {
          ID: 'Y105',
          title: 'Minimum Cost in November',
          period: '1 Month',
          target: '10.000.000',
          percent: '0%'
        }
      ]
    }
  }
}
</script>
