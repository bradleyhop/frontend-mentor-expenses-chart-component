<script>
export default {
  name: 'BarChart',

  props: {
    expJSON: {
      type     : Array,
      default  : () => [],
      required : true
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
    <!--
       - NB: height for charts is set here through style binding; same for all
       - viewports: max-height 150px
       -->
    <div
      v-for="expense in expJSON"
      :key="expense.id"
      class="bar-chart-container__bar"
      :style="{
        height: `${(expense.amount / maxExpense) * 150}px`
      }"
      :class="`${expense.amount === maxExpense ? 'max' : ''}`"
      :data-exp-amount="`${'$'.concat(expense.amount)}`"
    ></div>
  </div>

  <div class="bar-chart-container__legend">
    <div v-for="week in expJSON" :key="week.id">
      <p class="miniCaption day-title">{{ week.day }}</p>
    </div>
  </div>
</template>

<style lang="scss" scoped>
$bar-width-mobile: 33px;
$bar-width-desktop: 50.36px;
$transition-type: 0.2s ease;

.bar-chart-container {
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
  padding-top: 11px;
  width: $bar-width-mobile;
  text-align: center;

  @include desktop-breakpoint {
    width: $bar-width-desktop;
    padding-top: 8px;
  }
}

.bar-chart-container__bar {
  position: relative; // needed for tooltip positioning
  background-color: $red;
  border-radius: 3px;
  width: $bar-width-mobile;
  transition: background-color $transition-type;

  @include desktop-breakpoint {
    width: $bar-width-desktop;
    border-radius: 5px;
  }

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

  // tooltip construction; no sytling for mobile
  &::before {
    content: attr(data-exp-amount);
    color: $cardWhite;
    background-color: $darkBrown;
    border-radius: 5px;
    opacity: 0;
    padding: 8px;
    // positioning
    position: absolute;
    top: -42px;
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
