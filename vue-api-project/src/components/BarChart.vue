<template>
  <div class="container">
    <Bar v-if="loading" :data="chartData" />
  </div>
</template>

<script>
import { onMounted } from '@/views/HomeView.vue'
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  props:["chartData"],
  components: { Bar },
  data: () => ({
    deaths: [],
    deathYear:[],
    sex:[],
    leadCause:[],

  }),
  async mounted () {
    this.loading = false

    try {
      this.chartData = onMounted()

      this.loading = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>

<style scoped>

</style>