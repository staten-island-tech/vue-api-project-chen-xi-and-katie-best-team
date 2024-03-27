<template>
  <div>
    <h1>Circle Chart: Deaths Based on Diseases (1000 Deaths)</h1>
  </div>
  <div>
    <pieChart />
  </div>
</template>

<script>
import pieChart from '@/components/pieChart.vue'

export default {
  name: 'App',
  components: {
    pieChart
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
  background-color: #2a3c75;
  margin-top: 7rem;
  color: #a4b4e0;
}
</style>