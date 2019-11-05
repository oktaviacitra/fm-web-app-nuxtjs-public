<template>
  <v-card>
    <v-card-title>
      Invoice
      <v-divider
        class="mx-4"
        inset
        vertical
      />
      <v-spacer />
      <v-btn color="primary" dark class="mx-2" to="/feature/invoice/draft" v-on="on">
        New Invoice
      </v-btn>
    </v-card-title>
    <v-data-table
      :headers="headers"
      :items="desserts"
      :items-per-page="5"
      class="elevation-1"
    >
      <template v-slot:item.action="{ item }">
        <div class="text-center">
          <v-menu offset-y>
            <template v-slot:activator="{ on }">
              <v-btn
                color="primary"
                dark
                v-on="on"
              >
                Actions
              </v-btn>
            </template>
            <v-list>
              <v-list-item
                v-for="(item, index) in items"
                :key="index"
              >
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </div>
      </template>
    </v-data-table>
  </v-card>
</template>
<script>
export default {
  data () {
    return {
      items: [
        { title: 'Send Notification' },
        { title: 'Mark as Paid' }
      ],
      headers: [
        {
          text: 'Invoice ID',
          value: 'ID'
        },
        {
          text: 'Date',
          value: 'date'
        },
        {
          text: 'Send to',
          value: 'receiver'
        },
        {
          text: 'Due Date',
          value: 'deadline'
        },
        {
          text: 'Paid',
          value: 'paid'
        },
        {
          text: 'Status',
          value: 'status'
        },
        {
          text: 'Total Amount',
          value: 'total'
        },
        { text: 'Actions', value: 'action', sortable: false }
      ],
      desserts: [
        {
          ID: 'N101',
          date: '10/22/2018',
          receiver: 'Mayshella',
          deadline: '10/25/2018',
          paid: 'Paid',
          status: 'sent',
          total: '5.000.000'
        },
        {
          ID: 'N102',
          date: '10/25/2018',
          receiver: 'Mayshella',
          deadline: '10/28/2018',
          paid: 'Paid',
          status: 'sent',
          total: '5.000.000'
        },
        {
          ID: 'N103',
          date: '10/22/2018',
          receiver: 'Mayshella',
          deadline: '10/25/2018',
          paid: 'Paid',
          status: 'sent',
          total: '5.000.000'
        },
        {
          ID: 'N104',
          date: '11/02/2018',
          receiver: 'Mayshella',
          deadline: '11/05/2018',
          paid: 'Paid',
          status: 'sent',
          total: '5.000.000'
        },
        {
          ID: 'N105',
          date: '11/10/2018',
          receiver: 'Mayshella',
          deadline: '11/10/2018',
          paid: 'Paid',
          status: 'sent',
          total: '5.000.000'
        }
      ]
    }
  }
}
</script>
