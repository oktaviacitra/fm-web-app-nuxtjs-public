<template>
  <v-data-table
    :headers="headers"
    :items="desserts"
    sort-by="calories"
    class="elevation-1"
  >
    <template v-slot:top>
      <v-toolbar flat color="white">
        <v-toolbar-title>Loan</v-toolbar-title>
        <v-divider
          class="mx-4"
          inset
          vertical
        />
        <v-spacer />
        <v-dialog v-model="dialog" max-width="500px">
          <template v-slot:activator="{ on }">
            <v-btn color="primary" dark class="mb-2" v-on="on">
              <v-icon>mdi-plus</v-icon>
            </v-btn>
          </template>
          <v-card>
            <v-card-title>
              <span class="headline">{{ formTitle }}</span>
            </v-card-title>

            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12">
                    <v-text-field v-model="editedItem.account" label="Account Name" />
                    <v-text-field v-model="editedItem.from" label="From" />
                    <v-text-field v-model="editedItem.to" label="To" />
                    <v-textarea v-model="editedItem.description" label="Description" />
                    <v-text-field v-model="editedItem.status" label="Status" />
                    <v-text-field v-model="editedItem.amount" label="Amount" />
                    <v-text-field v-model="editedItem.date" label="Date" />
                    <v-text-field v-model="editedItem.deadline" label="Due Date" />
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>

            <v-card-actions>
              <v-spacer />
              <v-btn color="blue darken-1" text @click="close">
                Cancel
              </v-btn>
              <v-btn color="blue darken-1" text @click="save">
                Save
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-toolbar>
    </template>
    <template v-slot:item.action="{ item }">
      <v-icon
        small
        class="mr-2"
        @click="editItem(item)"
      >
        mdi-pencil
      </v-icon>
      <v-icon
        small
        @click="deleteItem(item)"
      >
        mdi-delete
      </v-icon>
      <v-icon small>
        mdi-marker-check
      </v-icon>
    </template>
  </v-data-table>
</template>
<script>
export default {
  data: () => ({
    dialog: false,
    headers: [
      {
        text: 'Date',
        align: 'left',
        sortable: false,
        value: 'date'
      },
      { text: 'Account', value: 'account' },
      { text: 'From', value: 'from' },
      { text: 'To', value: 'to' },
      { text: 'Description', value: 'description' },
      { text: 'Due Date', value: 'deadline' },
      { text: 'Status', value: 'status' },
      { text: 'Amount', value: 'amount' },
      { text: 'Actions', value: 'action', sortable: false }
    ],
    desserts: [],
    editedIndex: -1,
    editedItem: {
      date: '',
      account: '',
      from: '',
      to: '',
      description: '',
      deadline: '',
      status: '',
      amount: ''
    },
    defaultItem: {
      date: '',
      account: '',
      from: '',
      to: '',
      description: '',
      deadline: '',
      status: '',
      amount: ''
    }
  }),

  computed: {
    formTitle () {
      return this.editedIndex === -1 ? 'New Debt' : 'Edit Loan'
    }
  },

  watch: {
    dialog (val) {
      val || this.close()
    }
  },

  created () {
    this.initialize()
  },

  methods: {
    initialize () {
      this.desserts = [
        {
          date: '10/09/2018',
          account: 'Duty',
          from: 'Funding',
          to: 'Cash Budget',
          description: 'to complete finance',
          deadline: '10/20/2018',
          status: 'Unpaid',
          amount: '5.000.000'
        },
        {
          date: '10/09/2018',
          account: 'Duty',
          from: 'Funding',
          to: 'Cash Budget',
          description: 'to complete finance',
          deadline: '10/20/2018',
          status: 'Unpaid',
          amount: '5.000.000'
        },
        {
          date: '10/09/2018',
          account: 'Duty',
          from: 'Funding',
          to: 'Cash Budget',
          description: 'to complete finance',
          deadline: '10/20/2018',
          status: 'Unpaid',
          amount: '5.000.000'
        },
        {
          date: '10/09/2018',
          account: 'Duty',
          from: 'Funding',
          to: 'Cash Budget',
          description: 'to complete finance',
          deadline: '10/20/2018',
          status: 'Unpaid',
          amount: '5.000.000'
        },
        {
          date: '10/09/2018',
          account: 'Duty',
          from: 'Funding',
          to: 'Cash Budget',
          description: 'to complete finance',
          deadline: '10/20/2018',
          status: 'Unpaid',
          amount: '5.000.000'
        }
      ]
    },

    editItem (item) {
      this.editedIndex = this.desserts.indexOf(item)
      this.editedItem = Object.assign({}, item)
      this.dialog = true
    },

    deleteItem (item) {
      const index = this.desserts.indexOf(item)
      confirm('Are you sure you want to delete this item?') && this.desserts.splice(index, 1)
    },

    close () {
      this.dialog = false
      setTimeout(() => {
        this.editedItem = Object.assign({}, this.defaultItem)
        this.editedIndex = -1
      }, 300)
    },

    save () {
      if (this.editedIndex > -1) {
        Object.assign(this.desserts[this.editedIndex], this.editedItem)
      } else {
        this.desserts.push(this.editedItem)
      }
      this.close()
    }
  }
}
</script>
