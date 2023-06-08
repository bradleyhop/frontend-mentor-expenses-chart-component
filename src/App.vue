<script>
import ExpenseChart from './components/ExpenseChart.vue'

export default {
  name: 'App',

  components: {
    ExpenseChart
  }
}
</script>

<template>
  <main>
    <div class="expChartContainer">
      <ExpenseChart />
    </div>
  </main>

  <footer></footer>
</template>

<style lang="scss">
body {
  background-color: $creamBG;
}

.expChartContainer {
  min-height: 100vh;
  min-height: 100dvh;
  display: flex;
  align-items: center;
  justify-content: center;
}
</style>
