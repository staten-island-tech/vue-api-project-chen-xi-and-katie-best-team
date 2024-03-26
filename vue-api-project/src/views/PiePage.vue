<template>
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
</style>