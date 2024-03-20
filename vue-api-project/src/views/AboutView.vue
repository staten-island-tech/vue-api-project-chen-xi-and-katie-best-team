<template>
  <div>
    <testChart />
  </div>
</template>

<script >
/* import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
import apiChart from "@/components/apiChart.vue"
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

async function getDeaths(){
  try{
  let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json")
  let data = await get.json();
  return data
  } catch(error){
    console.log(error)
  }
}

export default {
  name: 'App',
  components: { apiChart },
  async mounted() {
    const data = await getDeaths()
    console.log(data);
  }
}
 */
 import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
import testChart from '@/components/testChart.vue'

export default {
  name: 'App',
  components: {
    testChart,
    Bar
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