<template>
  <div>
    <pieChart />
  </div>
</template>

<script >
import pieChart from '@/components/pieChart.vue'

export default {
  name: 'App',
  components: {
    pieChart
  },
}
</script>

<style scoped>
.container {
  width: 80vw;
  margin: 30px auto;
  display: flex;
  flex-wrap: wrap;
  flex-direction: row;
  align-items: center;
  justify-content: space-around;
}
</style>