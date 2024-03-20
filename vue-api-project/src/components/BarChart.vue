<template>
<div class="container">
    <Bar v-if="loaded" :data="apiData" :options="chartOptions"/> 

  </div>
</template>

<script>
import { ref, onBeforeMount } from "vue"
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)


export default {
  name: "BarChart",
  components: { Bar },
  data(){
    let loaded = ref();
    let death = ref([]);
    
async function getDeaths() {
  loaded.value === false;
  try {
    let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
    let data = await get.json();
    death.value = {
      chartData: {
        labels: [data[1].leading_cause,],
        apiData: [
          {
            label: 'Data One',
            backgroundColor: '#f87979',
            data: [data[1].deaths]
          }
        ]
      }
    } 
    console.log(death.value)
    loaded.value === true
  
  } catch (error) {
    console.log(error)
  }

};
onBeforeMount(getDeaths)
getDeaths();
return{
  death,
  loaded
}
  },
  chartOptions: {
  responsive: true,
  maintainAspectRatio: false
}
}


</script>

<style scoped>

</style>