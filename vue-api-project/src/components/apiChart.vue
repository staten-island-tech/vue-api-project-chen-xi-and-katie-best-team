<template>
  <div class="container">
    <Bar v-if="loaded" :data="chartData" />
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { ref } from 'vue'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'apiChart',
  components: { Bar },
  data: () => ({
    loaded: false,
    chartData: null,
  }),
  async mounted () {
    const loaded = ref();
    const death = ref([]);
    try {
      const response = await fetch('https://data.cityofnewyork.us/resource/jb7j-dtam.json');
      const data = await response.json();
      const chartData = data;
      death.map((dead => dead.value = {
      chartData: {
        labels: [chartData[1].leading_cause,],
        apiData: [
          {
            label: 'Data One',
            backgroundColor: '#f87979',
            data: [chartData[1].deaths]
          }
        ]
      }
    }))
    console.log(death)
    loaded.value == true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>