<template>
<div class="container">
    <Bar v-if="loaded" :data="chartData" /> 
  </div>
</template>

<script>
import { ref, onMounted } from "vue"
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)


export default {
  components: { Bar },
  setup(){
    const loaded = ref(true);
    const death = ref([]);

    
async function getDeaths() {
  try {
    let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
    let data = await get.json();
    death.value = {
      labels: data.deaths,
      apiData: [{
        label: "Common death",
        data: data.value,
      }]
    }
    loaded.value = true;

  
    console.log(death.value)
  } catch (error) {
    console.log(error)
  }

};
onMounted(getDeaths)
return{
  death
}
  }
}
</script>

<style scoped>

</style>