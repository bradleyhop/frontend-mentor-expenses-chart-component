<script>
// for this project, loading local json
import exp_json from '@/assets/data/data.json'
// bar chart component
import BarChart from './BarChart.vue'

export default {
  name: 'ExpenseChart',

  components: {
    BarChart
  },

  data() {
    return {
      expJSON: exp_json,
      // given as static data in project setup files
      balance: 921.48,
      monthlyTotalExpense: 478.33,
      percentChange: '+2.4%'
    }
  }
}
</script>

<template>
  <div class="expense-chart">
    <div class="balance-container">
      <div class="balance-content-container">
        <h1 class="bodyRegular balance-title">My balance</h1>
        <div class="headingL balance-number">&#36;{{ balance }}</div>
      </div>
      <div class="logo-img-container">
        <img src="@/assets/img/logo.svg" alt="logo" class="logo-img" />
      </div>
    </div>

    <div class="spending-container">
      <div class="headingL spending-title">Spending - Last 7 days</div>

      <div class="bar-chart-container">
        <BarChart :expJSON="expJSON" />
      </div>

      <hr class="divider" />

      <div class="monthly-container">
        <div class="total-month-container">
          <div class="bodyRegular monthly-title">Total this month</div>
          <div class="headingXL monthly-total-number">&#36;{{ monthlyTotalExpense }}</div>
        </div>
        <div class="percent-month-container">
          <div class="bodyBold percent-month-number">{{ percentChange }}</div>
          <div class="bodyRegular percent-month-title">from last month</div>
        </div>
      </div>
    </div>
  </div>
</template>

<style lang="scss" scoped>
.expense-chart {
  min-width: 540px;
}

.balance-container {
  background-color: $red;
  border-radius: 20px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  margin-bottom: 24px;
  min-height: 125px;
}

.balance-content-container {
  padding-left: 32px;
}

.balance-title {
  color: $white;
  line-height: 23.44px;
  margin-bottom: 8px;
}

.balance-number {
  color: $white;
  line-height: 41.66px;
}

.logo-img-container {
  padding-right: 39px;
}

.logo-img {
  height: 48px;
  width: 72px;
}

.spending-container {
  background-color: $cardWhite;
  border-radius: 20px;
  min-height: 511px;
  padding: 32px 40px 40px 40px;
}

.spending-title {
  color: $darkBrown;
  font-weight: 700;
  line-height: 41.66px;
}

hr.divider {
  border-top: 2px solid $creamBG;
  border-radius: 1px;
  margin: 32px 0;
}

.monthly-container {
  display: flex;
  justify-content: space-between;
}

.monthly-title {
  color: $medBrown;
  line-height: 23.44px;
}

.monthly-total-number {
  color: $darkBrown;
  font-weight: 700;
  line-height: 62.5px;
}

.percent-month-container {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: flex-end;
}

.percent-month-number {
  line-height: 23.44px;
}

.percent-month-title {
  color: $medBrown;
  line-height: 23.44px;
}
</style>
