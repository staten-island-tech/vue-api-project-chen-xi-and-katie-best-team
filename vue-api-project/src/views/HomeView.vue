<template>
  <div>
    <BarChart :data="chartData" :options="options" />
  </div>
</template>

<script>
import BarChart from '@/components/BarChart.vue'


export default {
  name: 'App',
  components: {
    BarChart
  },
  data() {
    return BarChart
  }
}

</script>

<style scoped></style>