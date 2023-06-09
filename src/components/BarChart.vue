<script>
export default {
  name: 'BarChart',

  props: {
    expJSON: {
      type: Array,
      default: () => [],
      required: true
    }
  },

  computed: {
    maxExpense() {
      return Math.max(...this.expJSON.map((exp) => exp.amount))
    }
  }
}
</script>

<template>
  <div id="barChartContainer" class="bar-chart-container">
    <div
      v-for="expense in expJSON"
      :key="expense.id"
      class="bar-chart-container__bar"
      :style="{
        height: `${(expense.amount / maxExpense) * 150}px`
      }"
      :class="`${expense.amount === maxExpense ? 'max' : ''}`"
    >
      <span data-text="$money" class="bodyBold bar-tooltip"></span>
    </div>
  </div>

  <div class="bar-chart-container__legend">
    <div v-for="days in expJSON" :key="days.id">
      <p class="miniCaption day-title">{{ days.day }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
$bar-width-desktop: 50.36px;

.bar-chart-container {
  min-height: 200px;
  display: flex;
  align-items: flex-end;
  justify-content: space-around;
}

.bar-chart-container__legend {
  @extend .bar-chart-container;
  min-height: initial;
}

.day-title {
  color: $medBrown;
  line-height: 19.53px;
  padding-top: 8px;
  width: $bar-width-desktop;
  text-align: center;
}

.bar-chart-container__bar {
  // for tooltip
  position: relative;
  display: inline-block;
  // end tooltip scaffold
  border-radius: 5px;
  width: $bar-width-desktop;
  background-color: $red;

  // max expenditure value get different color
  &.max {
    background-color: $cyan;

    &:hover {
      background-color: #b4e0e5;
    }
  }

  &:hover {
    cursor: pointer;
    background-color: #ff9b86;
  }

  .bar-tooltip {
    content: attr(data-text);
    position: absolute;
    top: -25%;
    //transform: translateY(-50%);
    width: 40px; // placeholder
    padding: 8px;
    color: $cardWhite;
    background-color: $darkBrown;
    border-radius: 5px;
    visibility: hidden;
    z-index: 1;

    &:hover {
      visibility: visible;
    }
  }
}
</style>
