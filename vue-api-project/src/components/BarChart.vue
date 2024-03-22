<template>
  <div class="container">
    <Bar v-if="loaded" :data="death" :width="1000" :height ="500"/>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import { Bar } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

export default {
  name: "barChart",
  components: { Bar },
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
              label: `Death Amounts`,
              backgroundColor: '#f87979',
              data: chartData
            }
          ]
        };
        chartData.push(data[i].deaths);
      }
    }
    }
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
.container{
  margin-top:2rem;
}
</style>