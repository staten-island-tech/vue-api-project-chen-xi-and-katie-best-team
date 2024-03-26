<template>
  <div>
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
  align-content: center;
  text-align: center;
}
</style>