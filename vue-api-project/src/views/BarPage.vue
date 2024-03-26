<template>
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
.bar {
  display: flex;
  align-items: center;
  justify-content: center;
  text-align: center;
}
</style>