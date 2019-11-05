<template>
  <v-data-table
    :headers="headers"
    :items="desserts"
    sort-by="ID"
    class="elevation-1"
  >
    <template v-slot:top>
      <v-toolbar flat color="white">
        <v-toolbar-title>Staff</v-toolbar-title>
        <v-divider
          class="mx-4"
          inset
          vertical
        />
        <v-spacer />
        <v-dialog v-model="dialog" max-width="500px">
          <template v-slot:activator="{ on }">
            <v-btn color="primary" dark class="mx-2" v-on="on">
              <v-icon dark>
                mdi-plus
              </v-icon>
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
                    <v-text-field v-model="editedItem.ID" label="Staff ID" />
                    <v-text-field v-model="editedItem.name" label="Staff Name" />
                    <v-text-field v-model="editedItem.email" label="Staff Email" />
                    <v-select
                      v-model="editedItem.job"
                      :items="['UI Designer', 'UX Designer', 'Front-end Developer', 'Back-end Developer']"
                      label="Job Category"
                      required
                    />
                    <v-text-field v-model="editedItem.total" label="Total PBI Done" type="number" />
                    <v-text-field v-model="editedItem.productivity" label="Productivity" />
                    <v-text-field v-model="editedItem.knowledge" label="Knowledge Score" type="number" />
                    <v-text-field v-model="editedItem.payroll" label="Payroll" />
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
        <v-dialog v-model="detailDialog" max-width="500px">
          <v-card>
            <v-card-title>
              <span class="headline">Detail</span>
            </v-card-title>

            <v-card-text>
              <v-list dense>
                <v-list-item>
                  <v-list-item-content>ID</v-list-item-content>
                  <v-list-item-content class="align-end">
                    {{ editedItem.ID }}
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-content>Name</v-list-item-content>
                  <v-list-item-content class="align-end">
                    {{ editedItem.name }}
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-content>Productivity</v-list-item-content>
                  <v-list-item-content class="align-end">
                    {{ editedItem.productivity }}
                  </v-list-item-content>
                </v-list-item>
                <v-list-item>
                  <v-list-item-content>PBI</v-list-item-content>
                  <v-list-item-content class="align-end">
                    Class Diagram<br>CDM PDM<br>Architecture Diagram
                  </v-list-item-content>
                </v-list-item>
                <!-- <v-list-item>
                  <v-expansion-panels>
                    <v-expansion-panel-header> PBI </v-expansion-panel-header>
                    <v-expansion-panel-content>Class Diagram</v-expansion-panel-content>
                    <v-expansion-panel-content>Architecture Diagram</v-expansion-panel-content>
                    <v-expansion-panel-content>CDM PDM</v-expansion-panel-content>
                  </v-expansion-panels>
                </v-list-item> -->
              </v-list>
            </v-card-text>

            <v-card-actions>
              <v-spacer />
              <v-btn color="blue darken-1" text @click="closeDetail">
                Close
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-toolbar>
    </template>
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
            <v-list-item>
              <v-list-item-title @click="editItem(item)">
                Edit
              </v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title @click="deleteItem(item)">
                Delete
              </v-list-item-title>
            </v-list-item>
            <v-list-item>
              <v-list-item-title @click="openDetail(item)">
                Detail
              </v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>
      </div>
    </template>
    <!-- <template v-slot:item.action="{ item }">
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
    </template> -->
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
    detailDialog: false,
    headers: [
      {
        text: 'Staff ID',
        align: 'left',
        sortable: true,
        value: 'ID'
      },
      {
        text: 'Name',
        value: 'name'
      },
      {
        text: 'Email',
        value: 'email'
      },
      {
        text: 'Job',
        value: 'job'
      },
      {
        text: 'Total PBI Done',
        value: 'total'
      },
      {
        text: 'Productivity',
        value: 'productivity'
      },
      {
        text: 'Knowledge Score',
        value: 'knowledge'
      },
      {
        text: 'Payroll',
        value: 'payroll'
      },
      { text: 'Actions', value: 'action', sortable: false }
    ],
    desserts: [],
    editedIndex: -1,
    editedItem: {
      ID: '',
      name: '',
      email: '',
      job: '',
      total: 0,
      productivity: '',
      knowledge: 0,
      payroll: ''
    },
    defaultItem: {
      ID: '',
      name: '',
      email: '',
      job: '',
      total: 0,
      productivity: '',
      knowledge: 0,
      payroll: ''
    }
  }),

  computed: {
    formTitle () {
      return this.editedIndex === -1 ? 'New Staff' : 'Edit Staff'
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
          ID: '2110171001',
          name: 'Daegal Prayoga',
          email: 'daegal@monking.com',
          job: 'Fullstack Developer',
          total: 20,
          productivity: '30/48 hours',
          knowledge: 80,
          payroll: '8.000.000'
        },
        {
          ID: '2110171002',
          name: 'Wifda Munafatihia',
          email: 'wifda@monking.com',
          job: 'UX Designer',
          total: 20,
          productivity: '30/48 hours',
          knowledge: 80,
          payroll: '8.000.000'
        },
        {
          ID: '2110171004',
          name: 'Mayshella Ainun',
          email: 'mayshella@monking.com',
          job: 'Product Owner',
          total: 20,
          productivity: '30/48 hours',
          knowledge: 80,
          payroll: '8.000.000'
        },
        {
          ID: '2110171005',
          name: 'Zahiroh Marwadilla',
          email: 'irma@monking.com',
          job: 'Backend Developer',
          total: 20,
          productivity: '30/48 hours',
          knowledge: 80,
          payroll: '8.000.000'
        },
        {
          ID: '2110171018',
          name: 'Oktavia Citra',
          email: 'citra@monking.com',
          job: 'Front-end Developer',
          total: 20,
          productivity: '30/48 hours',
          knowledge: 80,
          payroll: '8.000.000'
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
    },
    openDetail (item) {
      this.detailDialog = true
      this.editedIndex = this.desserts.indexOf(item)
      this.editedItem = Object.assign({}, item)
    },

    closeDetail () {
      this.detailDialog = false
    }
  }
}
</script>
