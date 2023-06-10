<script>
import ExpenseReport from './components/ExpenseReport.vue'

export default {
  name: 'App',

  components: {
    ExpenseReport
  }
}
</script>

<template>
  <main>
    <div class="expChartContainer">
      <ExpenseReport />
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
