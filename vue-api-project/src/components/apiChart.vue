<template>
    <div class="container">
      <Bar v-if="loaded" :data="chartData" />
    </div>
  </template>
  
  <script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'apiChart',
  components: { Bar },

  data: () => ({
    loaded: false,
    chartData: {
      labels: [],
      datasets: []
    }
  }),
  async mounted () {
    this.loaded = false

    try {
      const getData = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json")
      let { userlist } = await getData.json();
      this.chartData = userlist
      this.data.chartData.labels = []
      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
  </script>