<template>
  <v-card>
    <v-card-title>
      Cash Flow
      <v-divider
        class="mx-4"
        inset
        vertical
      />
      <v-select
        :items="['Current', 'Last Period', 'All Period']"
        label="Sort By"
      />
      <v-spacer />
      <v-btn color="primary" dark class="mx-2" v-on="on">
        <v-icon>mdi-fullscreen</v-icon>
      </v-btn>
      <v-btn color="primary" dark class="mx-2" v-on="on">
        <v-icon>mdi-share-variant</v-icon>
      </v-btn>
      <v-btn color="primary" dark class="mx-2" v-on="on">
        <v-icon>mdi-printer</v-icon>
      </v-btn>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="desserts"
      :items-per-page="5"
      class="elevation-1"
    />
  </v-card>
</template>
<script>
export default {
  data () {
    return {
      headers: [
        {
          text: 'Cash Operational',
          value: 'operational'
        },
        {
          text: 'Amount',
          value: 'amount'
        }
      ],
      desserts: [
        {
          operational: 'Cash',
          amount: '1.000.000'
        },
        {
          operational: 'Service Selling to Customer',
          amount: '500.000'
        },
        {
          operational: 'Interest Income',
          amount: '5.000.000'
        },
        {
          operational: 'Expenses',
          amount: '500.0000'
        },
        {
          operational: 'Rent Expenses',
          amount: '800.0000'
        }
      ]
    }
  }
}
</script>
