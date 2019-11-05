<template>
  <v-container>
    <!-- <v-row>
        <v-col cols="12" sm="6" md="3">
          <v-card
            class="mx-auto"
          >
            <v-card-text>
              <div class="text--primary">
                <div class="subtitle-1 font-weight-medium ">
                  Total Item
                </div>
                <div class="display-1 font-weight-bold text-right">
                  456
                </div>
              </div>
            </v-card-text>
            <v-divider />
            <v-card-actions>
              <div class="caption">
                <v-icon color="grey lighten-1">
                  mdi-calendar-clock
                </v-icon> Last 24 hours
              </div>
              <v-btn icon v-on="on">
                <v-icon color="grey lighten-1">
                  mdi-dots-horizontal
                </v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
        <v-col cols="12" sm="6" md="3">
          <v-card
            class="mx-auto"
          >
            <v-card-text>
              <div class="text--primary">
                <div class="subtitle-1 font-weight-medium ">
                  Total Category
                </div>
                <div class="display-1 font-weight-bold text-right">
                  62
                </div>
              </div>
            </v-card-text>
            <v-divider />
            <v-card-actions>
              <div class="caption">
                <v-icon color="grey lighten-1">
                  mdi-calendar-clock
                </v-icon> Last 24 hours
              </div>
              <v-btn icon v-on="on">
                <v-icon color="grey lighten-1">
                  mdi-dots-horizontal
                </v-icon>
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-col>
      </v-row> -->
    <!-- <v-row justify="center">
        <v-dialog v-model="dialog" persistent max-width="600px">
          <template v-slot:activator="{ on }">
            <v-col cols="12" sm="6" md="12">
              <v-btn class="mx-2" fab dark color="indigo" v-on="on">
                <v-icon dark>
                  mdi-plus
                </v-icon>
              </v-btn>
            </v-col>
          </template>
          <v-card>
            <v-card-title>
              <span class="headline">Create New Product</span>
            </v-card-title>
            <v-card-text>
              <v-container>
                <v-row>
                  <v-col cols="12">
                    <v-text-field label="Name" type="text" required />
                    <v-text-field label="Price" type="number" required />
                    <v-select
                      :items="['Machine Learning', 'Image Processing', 'Data Mining', 'Block Chain']"
                      label="Category"
                      required
                    />
                  </v-col>
                </v-row>
              </v-container>
            </v-card-text>
            <v-card-actions>
              <v-spacer />
              <v-btn color="blue darken-1" text @click="dialog = false">
                Close
              </v-btn>
              <v-btn color="blue darken-1" text @click="dialog = false">
                Save
              </v-btn>
            </v-card-actions>
          </v-card>
        </v-dialog>
      </v-row> -->
    <v-row>
      <v-col cols="12" sm="6" md="8">
        <ProductCRUD />
        <!-- <template>
            <v-data-table
              :headers="productHeaders"
              :items="products"
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
                  <v-dialog v-model="productDialog" max-width="500px">
                    <template v-slot:activator="{ on }">
                      <v-btn color="primary" dark class="mx-2" v-on="on">
                        <v-icon dark>
                          mdi-plus
                        </v-icon>
                      </v-btn>
                    </template>
                    <v-card>
                      <v-card-title>
                        <span class="headline">{{ productFormTitle }}</span>
                      </v-card-title>

                      <v-card-text>
                        <v-container>
                          <v-row>
                            <v-col cols="12">
                              <v-text-field v-model="editedProduct.ID" label="Product ID" type="text" />
                              <v-text-field v-model="editedProduct.name" label="Product Name" type="text" />
                              <v-select
                                :items="['Machine Learning', 'Image Processing', 'Data Mining', 'Block Chain']"
                                label="Product Category"
                                required
                              />
                              <v-text-field v-model="editedProduct.price" label="Product Price" type="text" />
                            </v-col>
                          </v-row>
                        </v-container>
                      </v-card-text>

                      <v-card-actions>
                        <v-spacer />
                        <v-btn color="blue darken-1" text @click="closeProduct">
                          Cancel
                        </v-btn>
                        <v-btn color="blue darken-1" text @click="saveProduct">
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
                  @click="editProduct(item)"
                >
                  mdi-pencil
                </v-icon>
                <v-icon
                  small
                  @click="deleteProduct(item)"
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
          </template> -->
        <!-- <v-card
            class="mx-auto"
            outlined
          >
            <v-card-title>
              Products
              <v-spacer />
            </v-card-title>
            <v-data-table
              :headers="productTitle"
              :items="productContent"
              :items-per-page="5"
              class="elevation-1"
            />
          </v-card> -->
      </v-col>
      <v-col cols="12" sm="6" md="4">
        <CategoryCRUD />
        <!-- <template>
            <v-data-table
              :headers="categoryHeaders"
              :items="categories"
              sort-by="ID"
              class="elevation-1"
            >
              <template v-slot:top>
                <v-toolbar flat color="white">
                  <v-toolbar-title>Category</v-toolbar-title>
                  <v-divider
                    class="mx-4"
                    inset
                    vertical
                  />
                  <v-spacer />
                  <v-dialog v-model="categoryDialog" max-width="500px">
                    <template v-slot:activator="{ on }">
                      <v-btn color="primary" dark class="mx-2" v-on="on">
                        <v-icon dark>
                          mdi-plus
                        </v-icon>
                      </v-btn>
                    </template>
                    <v-card>
                      <v-card-title>
                        <span class="headline">{{ categoryFormTitle }}</span>
                      </v-card-title>

                      <v-card-text>
                        <v-container>
                          <v-row>
                            <v-col cols="12">
                              <v-text-field v-model="editedCategory.ID" label="Category ID" type="text" />
                              <v-text-field v-model="editedCategory.name" label="Category Name" type="text" />
                            </v-col>
                          </v-row>
                        </v-container>
                      </v-card-text>

                      <v-card-actions>
                        <v-spacer />
                        <v-btn color="blue darken-1" text @click="closeCategory">
                          Cancel
                        </v-btn>
                        <v-btn color="blue darken-1" text @click="saveCategory">
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
                  @click="editCategory(item)"
                >
                  mdi-pencil
                </v-icon>
                <v-icon
                  small
                  @click="deleteCategory(item)"
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
          </template> -->
      </v-col>
      <!-- <v-col cols="12" sm="6" md="4">
          <v-card
            class="mx-auto"
            outlined
          >
            <v-card-title>
              Category
              <v-spacer />
            </v-card-title>
            <v-data-table
              :headers="categoryTitle"
              :items="categoryContent"
              :items-per-page="5"
              class="elevation-1"
            />
          </v-card>
        </v-col> -->
    </v-row>
  </v-container>
</template>

<script>
import ProductCRUD from '@/components/ProductCRUD'
import CategoryCRUD from '@/components/CategoryCRUD'
export default {
  components: {
    ProductCRUD,
    CategoryCRUD
  }
}

// export default {
//   head () {
//     return {
//       title: 'Product'
//     }
//   },
//   data: () => ({
//     productDialog: false,
//     categoryDialog: false,
//     productHeaders: [
//       {
//         text: 'Product ID',
//         align: 'left',
//         sortable: true,
//         value: 'ID'
//       },
//       {
//         text: 'Name',
//         value: 'name'
//       },
//       {
//         text: 'Category',
//         value: 'category'
//       },
//       {
//         text: 'Price',
//         value: 'price'
//       },
//       { text: 'Actions', value: 'action', sortable: false }
//     ],
//     categoryHeaders: [
//       {
//         text: 'Category ID',
//         align: 'left',
//         sortable: true,
//         value: 'ID'
//       },
//       {
//         text: 'Name',
//         value: 'name'
//       },
//       { text: 'Actions', value: 'action', sortable: false }
//     ],
//     products: [],
//     categories: [],
//     editedIndex: -1,
//     editedProduct: {
//       ID: '',
//       name: '',
//       category: '',
//       price: ''
//     },
//     defaultProduct: {
//       ID: '',
//       name: '',
//       category: '',
//       price: ''
//     },
//     editedCategory: {
//       ID: '',
//       name: ''
//     },
//     defaultCategory: {
//       ID: '',
//       name: ''
//     }
//   }),
//   computed: {
//     productFormTitle () {
//       return this.editedIndex === -1 ? 'New Product' : 'Edit Product'
//     },
//     categoryFormTitle () {
//       return this.editedIndex === -1 ? 'New Category' : 'Edit Category'
//     }
//   },
//   watch: {
//     productDialog (val) {
//       val || this.closeProduct()
//     },
//     categoryDialog (val) {
//       val || this.closeCategory()
//     }
//   },
//   created () {
//     this.initialize()
//   },
//   methods: {
//     initialize () {
//       this.products = [
//         {
//           ID: 'C101',
//           name: 'Mencari Cinta',
//           category: 'Machine Learning',
//           price: '10.000.000'
//         },
//         {
//           ID: 'C102',
//           name: 'Mencari Jodoh',
//           category: 'Machine Learning',
//           price: '15.000.000'
//         },
//         {
//           ID: 'C103',
//           name: 'Suami Tampan',
//           category: 'Image Processing',
//           price: '15.000.000'
//         },
//         {
//           ID: 'C104',
//           name: 'Istri Cantik',
//           category: 'Image Processing',
//           price: '15.000.000'
//         },
//         {
//           ID: 'C105',
//           name: 'Semakin Cinta',
//           category: 'Machine Learning',
//           price: '15.000.000'
//         }
//       ]
//       this.categories = [
//         {
//           ID: 'A101',
//           name: 'Machine Learning'
//         },
//         {
//           ID: 'A102',
//           name: 'Data Mining'
//         },
//         {
//           ID: 'A103',
//           name: 'Block Chain'
//         },
//         {
//           ID: 'A104',
//           name: 'Internet of Things'
//         },
//         {
//           ID: 'A105',
//           name: 'Image Processing'
//         }
//       ]
//     }
//   },
//   editProduct (item) {
//     this.editedIndex = this.products.indexOf(item)
//     this.editedProduct = Object.assign({}, item)
//     this.productDialog = true
//   },
//   deleteProduct (item) {
//     const index = this.products.indexOf(item)
//     confirm('Are you sure want to delete this product?') && this.products.splice(index, 1)
//   },
//   closeProduct () {
//     this.productDialog = false
//     setTimeout(() => {
//       this.editedProduct = Object.assign({}, this.defaultProduct)
//       this.editedIndex = -1
//     }, 300)
//   },
//   saveProduct () {
//     if (this.editedIndex > -1) {
//       Object.assign(this.products[this.editedIndex], this.editedProduct)
//     } else {
//       this.products.push(this.editedProduct)
//     }
//     this.closeProduct()
//   },
//   editCategory (category) {
//     this.editedIndex = this.categories.indexOf(category)
//     this.editedCategory = Object.assign({}, category)
//     this.categoryDialog = true
//   },
//   deleteCategory (category) {
//     const index = this.categories.indexOf(category)
//     confirm('Are you sure you want to delete this category?') && this.categories.splice(index, 1)
//   },
//   closeCategory () {
//     this.categoryDialog = false
//     setTimeout(() => {
//       this.editedCategory = Object.assign({}, this.defaultCategory)
//       this.editedIndex = -1
//     })
//   },
//   saveCategory () {
//     if (this.editedIndex > -1) {
//       Object.assign(this.categories[this.editedIndex], this.editedCategory)
//     } else {
//       this.categories.push(this.editedCategory)
//     }
//     this.closeCategory()
//   }
// }
</script>

<style lang="scss" scoped>
.grid {
  display: grid;
  row-gap: 2rem;
}
</style>
