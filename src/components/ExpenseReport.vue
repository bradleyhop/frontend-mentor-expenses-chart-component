<script>
// for this project, loading local json
import exp_json from '@/assets/data/data.json'
// bar chart component
import BarChart from './BarChart.vue'

export default {
  name: 'ExpenseReport',

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
// spin animation for logo
@keyframes spin {
  from{
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.expense-chart {
  min-width: 343px;

  @include desktop-breakpoint {
    min-width: 540px;
  }
}

.balance-container {
  background-color: $red;
  border-radius: 10px;
  display: flex;
  align-items: center;
  margin-bottom: 16px;
  min-height: 97px;
  justify-content: space-between;

  @include desktop-breakpoint {
    border-radius: 20px;
    margin-bottom: 24px;
    min-height: 125px;
  }
}

.balance-content-container {
  padding-left: 20px;

  @include desktop-breakpoint {
    padding-left: 32px;
  }
}

.balance-title {
  color: $white;
  margin-bottom: 4px;

  @include desktop-breakpoint {
    margin-bottom: 8px;
  }
}

.balance-number {
  color: $white;
}

.logo-img-container {
  padding-right: 24px;

  @include desktop-breakpoint {
    padding-right: 39px;
  }
}

.logo-img {
  height: 40px;
  width: 60px;

  @include desktop-breakpoint {
    height: 48px;
    width: 72px;
  }

  &:hover {
    // an easter egg
    animation: spin 850ms ease-in-out 1;
  }
}

.spending-container {
  background-color: $cardWhite;
  border-radius: 10px;
  min-height: 421px;
  padding: 24px 20px;

  @include desktop-breakpoint {
    border-radius: 20px;
    min-height: 511px;
    padding: 32px 40px 40px 40px;
  }
}

.spending-title {
  color: $darkBrown;
  font-weight: 700;
}

hr.divider {
  border-top: 2px solid $creamBG;
  border-radius: 1px;
  margin: 24px 0;

  @include desktop-breakpoint {
    margin: 32px 0;
  }
}

.monthly-container {
  display: flex;
  justify-content: space-between;
}

.monthly-title {
  color: $medBrown;
}

.monthly-total-number {
  color: $darkBrown;
  font-weight: 700;
}

.percent-month-container {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  justify-content: flex-end;
}

.percent-month-title {
  color: $medBrown;
}
</style>
