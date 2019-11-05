<template>
  <v-data-table
    :headers="headers"
    :items="desserts"
    :items-per-page="5"
    class="elevation-1"
  />
</template>
<script>
export default {
  data () {
    return {
      headers: [
        {
          text: 'Account ID',
          align: 'left',
          sortable: false,
          value: 'ID'
        },
        { text: 'Name', value: 'name' },
        { text: 'Category', value: 'category' },
        { text: 'Activity', value: 'activity' }
      ],
      desserts: [
        {
          ID: 'Q101',
          name: 'Love\'s Profit',
          category: 'Property',
          activity: '15.000.000'
        },
        {
          ID: 'Q102',
          name: 'Bird\'s Profit',
          category: 'Property',
          activity: '15.000.000'
        },
        {
          ID: 'Q103',
          name: 'Food\'s Profit',
          category: 'Property',
          activity: '15.000.000'
        },
        {
          ID: 'Q104',
          name: 'Bunny\'s Profit',
          category: 'Property',
          activity: '15.000.000'
        },
        {
          ID: 'Q105',
          name: 'Pearl\'s Profit',
          category: 'Property',
          activity: '15.000.000'
        }
      ]
    }
  }
}
</script>
