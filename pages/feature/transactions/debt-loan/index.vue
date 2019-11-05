<template>
  <v-container>
    <v-row>
      <v-col cols="12" sm="6" md="3">
        <v-card
          class="mx-auto"
        >
          <v-card-text>
            <div class="text--primary">
              <div class="subtitle-1 font-weight-medium ">
                Cash Out for Debt
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
                Cash In from Loan
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
                Unpaid Debt
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
                Unpaid Loan
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
        <no-ssr>
          <v-card
            class="mx-auto"
          >
            <v-card-text>
              <ChartBar />
            </v-card-text>
          </v-card>
        </no-ssr>
      </v-col>
    </v-row>
    <v-row>
      <v-col cols="12" sm="6" md="4">
        <v-card
          class="mx-auto"
        >
          <v-card-text>
            <div class="text--primary">
              <div class="subtitle-1 font-weight-medium ">
                Total Debt
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
      <v-col cols="12" sm="6" md="4">
        <v-card
          class="mx-auto"
        >
          <v-card-text>
            <div class="text--primary">
              <div class="subtitle-1 font-weight-medium ">
                Total Loan
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
      <v-col cols="12" sm="6" md="4">
        <v-card
          class="mx-auto"
        >
          <v-card-title>Solvability Ratio</v-card-title>
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
      <v-row>
        <v-col cols="12">
          <DebtCRUD />
        </v-col>
        <v-col cols="12">
          <LoanCRUD />
        </v-col>
      </v-row>
    </v-row>
  </v-container>
</template>
<script>
import DebtCRUD from '@/components/DebtCRUD'
import LoanCRUD from '@/components/LoanCRUD'
import ChartBar from '@/components/chart-bar'
export default {
  components: {
    DebtCRUD,
    LoanCRUD,
    ChartBar
  },
  data () {
    return {
      interval: {},
      value: 0
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
