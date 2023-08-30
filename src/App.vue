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
      <p class="attribution">
        Challenge by
        <a
          href="https://www.frontendmentor.io/challenges/expenses-chart-component-e7yJBUdjwt"
          class="attr-link"
          target="_blank"
          rel="noreferrer noopener"
          >Frontend Mentor</a
        ><br />
        Code by
        <a
          href="https://github.com/bradleyhop/frontend-mentor-expenses-chart-component"
          class="attr-link"
          target="_blank"
          rel="noreferrer noopener"
          >Bradley Smith</a
        >
      </p>
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
  flex-direction: column;
}

.attribution {
  color: $darkBrown;
  margin-top: 1rem;
  font-size: 1.1rem;
  text-align: center;
  line-height: 1.5rem;
}

.attr-link {
  text-decoration: underline;
}
</style>
