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
          name: 'Love\'s Cost',
          category: 'Property',
          activity: '15.000'
        },
        {
          ID: 'Q102',
          name: 'Bird\'s Cost',
          category: 'Property',
          activity: '15.000'
        },
        {
          ID: 'Q103',
          name: 'Food\'s Cost',
          category: 'Property',
          activity: '15.000'
        },
        {
          ID: 'Q104',
          name: 'Bunny\'s Cost',
          category: 'Property',
          activity: '15.000'
        },
        {
          ID: 'Q105',
          name: 'Pearl\'s Cost',
          category: 'Property',
          activity: '15.000'
        }
      ]
    }
  }
}
</script>
