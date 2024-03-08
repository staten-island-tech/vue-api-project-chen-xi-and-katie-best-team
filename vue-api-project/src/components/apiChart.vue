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
      chartData: null,
      label: 'Deaths',
    }),
    async mounted () {
      this.loaded = false
  
      try {
        const { userlist } = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json")
        this.chartdata = userlist
  
        this.loaded = true
      } catch (e) {
        console.error(e)
      }
    }
  }
  </script>