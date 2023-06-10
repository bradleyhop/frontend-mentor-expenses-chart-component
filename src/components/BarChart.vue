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
      :exp-amount="`${'$'.concat(expense.amount)}`"
    ></div>
  </div>

  <div class="bar-chart-container__legend">
    <div v-for="week in expJSON" :key="week.id">
      <p class="miniCaption day-title">{{ week.day }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
$bar-width-desktop: 50.36px;
$transition-type: 0.2s ease;

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
  // tooltip
  position: relative;
  //
  background-color: $red;
  border-radius: 5px;
  width: $bar-width-desktop;
  transition: background-color $transition-type;

  &:hover {
    cursor: pointer;
    background-color: #ff9b86;
  }

  // max expenditure value gets different color
  &.max {
    background-color: $cyan;

    &:hover {
      background-color: #b4e0e5;
    }
  }

  // tooltip construction
  &::before {
    content: attr(exp-amount);
    color: $cardWhite;
    background-color: $darkBrown;
    border-radius: 5px;
    opacity: 0;
    padding: 8px;
    // positioning
    position: absolute;
    top: -2.6rem;
    left: 50%;
    transform: translateX(-50%);
    transition: opacity $transition-type;
  }

  // show tooltip
  &:hover::before {
    opacity: 1;
  }
}
</style>
