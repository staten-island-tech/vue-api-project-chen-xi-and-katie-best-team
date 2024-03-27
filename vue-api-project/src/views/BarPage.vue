<template>
  <div>
    <h1>Bar Chart: Leading Causes of Death</h1>
  </div>
  <div class="bar">
    <barChart />
  </div>
</template>

<script>
import barChart from '@/components/BarChart.vue'

export default {
  name: 'App',
  components: {
    barChart
  },
}

</script>

<style scoped>
div {
    width: 100%;
  }
  h1 {
  text-align: center;
  font-size: 22px;
  background-color: #2c4e8b;
  margin-top: 7rem;
  color: rgb(207, 220, 236);
}
</style>