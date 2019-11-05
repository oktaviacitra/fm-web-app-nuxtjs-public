<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-breadcrumbs :items="items" large />
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12">
        <v-tabs>
          <v-tab>Cash In</v-tab>
          <v-tab>Profit Centered</v-tab>
          <v-tab-item class="pa-md-4">
            <v-row>
              <v-col cols="8">
                <v-card>
                  <v-card-text>
                    <ChartBar />
                  </v-card-text>
                </v-card>
              </v-col>
              <v-col cols="4">
                <v-card>
                  <v-card-title>Cash In Analysis</v-card-title>
                  <v-card-text>
                    <div class="text-center">
                      <v-progress-circular
                        :rotate="360"
                        :size="100"
                        :width="15"
                        :value="value"
                        color="teal"
                      >
                        {{ value }}
                      </v-progress-circular>
                    </div>
                  </v-card-text>
                </v-card>
              </v-col>
            </v-row>
            <v-row>
              <v-col cols="8">
                <CashInCRUD />
              </v-col>
              <v-col cols="4">
                <AccountCRUD />
              </v-col>
            </v-row>
          </v-tab-item>
          <v-tab-item class="pa-md-4">
            <v-row>
              <v-col cols="12">
                <v-spacer />
                <ProfitHistory />
              </v-col>
            </v-row>
            <v-card class="pa-md-4 mx-lg-auto">
              <v-card-text>
                <v-row>
                  <v-col cols="8">
                    <div class="font-weight-medium title">
                      Progress
                    </div>
                    <div class="display-2 font-weight-bold">
                      60%
                    </div>
                    <v-progress-linear
                      v-model="knowledge"
                      height="35"
                      reactive
                    >
                      <strong>300.000/3.000.000</strong>
                    </v-progress-linear>
                  </v-col>
                  <v-col cols="4">
                    <div>Title</div>
                    <div class="font-weight-medium title">
                      Goals in October
                    </div>
                    <div><br></div>
                    <div>Period</div>
                    <div class="font-weight-medium title">
                      1 Month
                    </div>
                  </v-col>
                </v-row>
              </v-card-text>
            </v-card>
            <v-row>
              <v-col cols="8">
                <ProfitTable />
              </v-col>
              <v-col cols="4">
                <AccountCRUD />
              </v-col>
            </v-row>
          </v-tab-item>
        </v-tabs>
      </v-col>
    </v-row>
  </v-container>
</template>
<script>
import CashInCRUD from '@/components/CashInCRUD'
import ChartBar from '@/components/chart-bar'
import AccountCRUD from '@/components/AccountCRUD'
import ProfitTable from '@/components/ProfitTable'
import ProfitHistory from '@/components/ProfitHistory'

export default {
  components: {
    CashInCRUD,
    ChartBar,
    AccountCRUD,
    ProfitTable,
    ProfitHistory
  },
  data () {
    return {
      knowledge: 60,
      interval: {},
      value: 0,
      items: [
        {
          text: 'Dashboard',
          disabled: false,
          href: 'breadcrumbs_dashboard'
        },
        {
          text: 'Transactions',
          disabled: false,
          href: 'breadcrumbs_link_1'
        },
        {
          text: 'Cash In',
          disabled: true,
          href: 'breadcrumbs_link_2'
        }
      ]
    }
  },
  beforeDestroy () {
    clearInterval(this.interval)
  },
  mounted () {
    this.interval = setInterval(() => {
      if (this.value === 100) {
        return (this.value = 0)
      }
      this.value += 10
    }, 1000)
  }
}
</script>
<style scoped>
.v-progress-circular {
  margin: 1rem;
}
</style>
