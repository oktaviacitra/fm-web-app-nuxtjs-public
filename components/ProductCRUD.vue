<template>
  <v-data-table
    :headers="headers"
    :items="desserts"
    sort-by="ID"
    class="elevation-1"
  >
    <template v-slot:top>
      <v-toolbar flat color="white">
        <v-toolbar-title>Product</v-toolbar-title>
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
                    <v-text-field v-model="editedItem.ID" label="Product ID" />
                    <v-text-field v-model="editedItem.name" label="Product name" />
                    <v-text-field v-model="editedItem.price" label="Product price" />
                    <v-select
                      v-model="editedItem.category"
                      :items="['Machine Learning', 'Image Processing', 'Data Mining', 'Block Chain']"
                      label="Product Category"
                      required
                    />
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
        text: 'Product ID',
        align: 'left',
        sortable: true,
        value: 'ID'
      },
      {
        text: 'Name',
        value: 'name'
      },
      {
        text: 'Category',
        value: 'category'
      },
      {
        text: 'Price',
        value: 'price'
      },
      { text: 'Actions', value: 'action', sortable: false }
    ],
    desserts: [],
    editedIndex: -1,
    editedItem: {
      ID: '',
      name: '',
      category: '',
      price: ''
    },
    defaultItem: {
      ID: '',
      name: '',
      category: '',
      price: ''
    }
  }),

  computed: {
    formTitle () {
      return this.editedIndex === -1 ? 'New Product' : 'Edit Product'
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
          ID: 'C101',
          name: 'Mencari Cinta',
          category: 'Machine Learning',
          price: '10.000.000'
        },
        {
          ID: 'C102',
          name: 'Mencari Jodoh',
          category: 'Machine Learning',
          price: '15.000.000'
        },
        {
          ID: 'C103',
          name: 'Suami Tampan',
          category: 'Image Processing',
          price: '15.000.000'
        },
        {
          ID: 'C104',
          name: 'Istri Cantik',
          category: 'Image Processing',
          price: '15.000.000'
        },
        {
          ID: 'C105',
          name: 'Semakin Cinta',
          category: 'Machine Learning',
          price: '15.000.000'
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
