<template>
    <div class="container">
    <apiChart />
  </div>
</template>

<script>
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
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
  }}

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