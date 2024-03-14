<template>
  <div>
    <apiChart />
  </div>
</template>

<script >
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
import apiChart from "@/components/apiChart.vue"
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

async function getDeaths(){
  try{
  let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json")
  let data = await get.json();
  console.log(data)
  return data
  } catch(error){
    console.log(error)
  }
}
getDeaths();
export default {
  name: 'App',
  components: { apiChart },
}

</script>

<style scoped>

</style>