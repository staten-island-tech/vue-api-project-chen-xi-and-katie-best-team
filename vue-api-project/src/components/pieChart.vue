<template>
  <div class="container" >
    <Pie v-if="loaded" :data="death" :width="300" :height="300"/>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import { Pie } from 'vue-chartjs';
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from "chart.js";

ChartJS.register(ArcElement, Tooltip, Legend);

export default {
  name: "pieChart",
  components: { Pie },
  setup() {
    const loaded = ref(false);
    const death = ref({});

    async function getDeaths() {
      try {
        let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
        let data = await get.json();
        const labels = [];
        const chartData = []; 
          for (let i = 0; i < 100; i++) {
            if (data[i] && data[i].leading_cause) {
              if(data[i].deaths >= 100){
              labels.push(data[i].leading_cause);
          
        
        death.value = {
          labels: labels,
          datasets: [
            {
              label: 'Data One',
              backgroundColor: '#f87979',
              data: chartData
            }
          ]
        };
        chartData.push(data[i].deaths);
      }
    }
    }
        console.log(death.value);
        loaded.value = true;
      } catch (error) {
        console.log(error);
      }
    }

    onMounted(getDeaths);

    return {
      death,
      loaded,
    };
  },
  }
</script>

<style scoped>

</style>