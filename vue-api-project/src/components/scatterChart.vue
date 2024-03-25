<template>
    <Scatter class = "place" v-if="loaded" :data="death" :width="300" :height="300" />
</template>

<script>
import { ref, onMounted } from "vue"
import {
  Chart as ChartJS,
  LinearScale,
  PointElement,
  LineElement,
  Tooltip,
  Legend
} from 'chart.js'
import { Scatter } from 'vue-chartjs'

ChartJS.register(LinearScale, PointElement, LineElement, Tooltip, Legend)

export default {
  name: "scatterChart",
  components: { Scatter },
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
          if (data[i] && data[i].death_rate) {
            if (data[i].year >= 100) {
              labels.push(data[i].death_rate);


              death.value = {
                labels: labels,
                datasets: [
                  {
                    label: 'Death Amounts Compared to Death Rate',
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
.place{
  margin-top:5rem;
}</style>