<template>
  <div class="container">
    <Bar v-if="loaded" :data="death" :width="600"/>
  </div>
</template>

<script>
import { ref, onMounted } from "vue";
import { Bar } from 'vue-chartjs';
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js';

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

export default {
  name: "apiChart",
  components: { Bar },
  setup() {
    const loaded = ref(false);
    const death = ref({});

    async function getDeaths() {
      try {
        let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
        let data = await get.json();
        const labels = [];
          for (let i = 0; i < 10; i++) {
            if (data[i] && data[i].leading_cause) {
              labels.push(data[i].leading_cause);
          }
        }
        death.value = {
          labels: labels,
          datasets: [
            {
              label: 'Data One',
              backgroundColor: '#f87979',
              data: [data[1].deaths]
            }
          ]
        };
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
.container {
  padding: 8rem;
  margin: 0px auto;
  
}
</style>