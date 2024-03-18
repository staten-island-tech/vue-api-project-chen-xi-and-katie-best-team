<template>
  <div>
    <BarChart/>
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
import BarChart from '@/components/BarChart.vue'
import * as Chardata from '@/components/BarChart.vue'

export default {
  name: 'App',
  components: {
    BarChart,
    Bar
  },
  data() {
    return Chardata
  }
}

</script>

<style scoped></style>