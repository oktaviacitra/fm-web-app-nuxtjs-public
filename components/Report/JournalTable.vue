<template>
  <v-card>
    <v-card-title>
      Journal
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
          text: 'Date',
          value: 'date'
        },
        { text: 'Description', value: 'description' },
        { text: 'Reference', value: 'reference' },
        { text: 'Debt', value: 'debt' },
        { text: 'Kredit', value: 'kredit' }
      ],
      desserts: [
        {
          date: '10/09/2018',
          description: 'Cash',
          reference: '100',
          debt: 'cash flow',
          kredit: '5.000.000'
        },
        {
          date: '10/11/2018',
          description: 'Cash',
          reference: '110',
          debt: 'cash flow',
          kredit: '6.000.000'
        },
        {
          date: '10/15/2018',
          description: 'Cash',
          reference: '111',
          debt: 'cash flow',
          kredit: '5.500.000'
        },
        {
          date: '10/20/2018',
          description: 'Cash',
          reference: '140',
          debt: 'cash flow',
          kredit: '5.600.000'
        },
        {
          date: '10/28/2018',
          description: 'Cash',
          reference: '100',
          debt: 'cash flow',
          kredit: '5.000.000'
        }
      ]
    }
  }
}
</script>
