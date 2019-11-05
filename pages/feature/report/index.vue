<template>
  <v-container>
    <v-tabs>
      <v-tab>All</v-tab>
      <v-tab>Journal</v-tab>
      <v-tab>Account</v-tab>
      <v-tab>Cash Flow</v-tab>
      <v-tab>Balance Sheet</v-tab>
      <v-tab>BProfit & Lost</v-tab>
      <v-tab-item>
        <v-row>
          <v-col cols="12">
            <JournalTable />
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <AccountTable />
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <CashFlowTable />
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <BalanceSheetTable />
          </v-col>
        </v-row>
        <v-row>
          <v-col cols="12">
            <ProfitLostTable />
          </v-col>
        </v-row>
      </v-tab-item>
      <v-tab-item>
        <v-row>
          <v-col cols="12">
            <JournalTable />
          </v-col>
        </v-row>
      </v-tab-item>
      <v-tab-item>
        <v-row>
          <v-col cols="12">
            <AccountTable />
          </v-col>
        </v-row>
      </v-tab-item>
      <v-tab-item>
        <v-row>
          <v-col cols="12">
            <CashFlowTable />
          </v-col>
        </v-row>
      </v-tab-item>
      <v-tab-item>
        <v-row>
          <v-col cols="12">
            <BalanceSheetTable />
          </v-col>
        </v-row>
      </v-tab-item>
      <v-tab-item>
        <v-row>
          <v-col cols="12">
            <ProfitLostTable />
          </v-col>
        </v-row>
      </v-tab-item>
    </v-tabs>
  </v-container>
</template>
<script>

import JournalTable from '@/components/Report/JournalTable'
import AccountTable from '@/components/Report/AccountTable'
import CashFlowTable from '@/components/Report/CashFlowTable'
import BalanceSheetTable from '@/components/Report/BalanceSheetTable'
import ProfitLostTable from '@/components/Report/ProfitLostTable'

export default {
  components: {
    JournalTable,
    AccountTable,
    CashFlowTable,
    BalanceSheetTable,
    ProfitLostTable
  }
}
</script>
