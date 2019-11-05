<template>
  <v-data-table
    :headers="headers"
    :items="desserts"
    sort-by="calories"
    class="elevation-1"
  >
    <template v-slot:top>
      <v-toolbar flat color="white">
        <v-toolbar-title>Cash Out</v-toolbar-title>
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
                    <v-text-field v-model="editedItem.title" label="Title" />
                    <v-text-field v-model="editedItem.date" label="Date" />
                    <v-text-field v-model="editedItem.account" label="Account" />
                    <v-text-field v-model="editedItem.to" label="To" />
                    <v-text-field v-model="editedItem.amount" label="Amount" />
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
    <template v-slot:no-data>
      <v-btn color="primary" @click="initialize">
        Reset
      </v-btn>
    </template>
  </v-data-table>
</template>
<script>
export default {
  data: () => ({
    dialog: false,
    headers: [
      {
        text: 'Title',
        align: 'left',
        sortable: false,
        value: 'title'
      },
      { text: 'Date', value: 'date' },
      { text: 'Account', value: 'account' },
      { text: 'To', value: 'to' },
      { text: 'Amount', value: 'amount' }
    ],
    desserts: [],
    editedIndex: -1,
    editedItem: {
      title: '',
      date: '',
      account: '',
      to: '',
      amount: ''
    },
    defaultItem: {
      title: '',
      date: '',
      account: '',
      to: '',
      amount: ''
    }
  }),

  computed: {
    formTitle () {
      return this.editedIndex === -1 ? 'New Cash Out' : 'Edit Cash Out'
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
          title: 'AdSense',
          date: '10/21/2018',
          account: 'Property',
          to: 'Bank Account',
          amount: '5.000.000'
        },
        {
          title: 'AdSense',
          date: '10/21/2018',
          account: 'Property',
          to: 'Bank Account',
          amount: '5.000.000'
        },
        {
          title: 'AdSense',
          date: '10/21/2018',
          account: 'Property',
          to: 'Bank Account',
          amount: '5.000.000'
        },
        {
          title: 'AdSense',
          date: '10/21/2018',
          account: 'Property',
          to: 'Bank Account',
          amount: '5.000.000'
        },
        {
          title: 'AdSense',
          date: '10/21/2018',
          account: 'Property',
          to: 'Bank Account',
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
