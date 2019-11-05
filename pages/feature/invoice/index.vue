<template>
  <no-ssr>
    <v-container>
      <v-row>
        <v-col cols="12" sm="6" md="3">
          <v-card
            class="mx-auto"
          >
            <v-card-text>
              <div class="text--primary">
                <div class="subtitle-1 font-weight-medium ">
                  Invoice from Income
                </div>
                <div class="display-1 font-weight-bold text-right">
                  Rp. 954.000
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
                  Loan from Invoice
                </div>
                <div class="display-1 font-weight-bold text-right">
                  Rp. 954.000
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
                  Unpaid Invoice
                </div>
                <div class="display-1 font-weight-bold text-right">
                  Rp. 954.000
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
                  Invoice Analysis
                </div>
                <div class="display-1 font-weight-bold text-right">
                  Rp. 954.000
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
      </v-row>
      <v-row>
        <v-col cols="12" sm="6" md="12">
          <InvoiceCRUD />
        </v-col>
      </v-row>
    </v-container>
  </no-ssr>
</template>

<script>
import InvoiceCRUD from '@/components/InvoiceCRUD'
export default {
  components: {
    InvoiceCRUD
  }
}
</script>

<style lang="scss" scoped>
.grid {
  display: grid;
  row-gap: 2rem;
}
</style>
