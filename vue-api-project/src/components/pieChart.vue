<template>
  <Pie class="place" v-if="loaded" :data="death" :width="600" :height="700" />
</template>

<script>
import { ref, onMounted } from "vue";
import { Pie } from 'vue-chartjs';
import { Chart as ChartJS, ArcElement, Tooltip, Legend } from "chart.js";
ChartJS.defaults.font.family = "Roboto Mono, monospace";
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
        const colors = [];
        const labels = [];
        const chartData = [];
        function getColor() {
          let color = Math.floor(Math.random() * 16777216).toString(16);
          colors.push('#000000'.slice(0, -color.length) + color)
        };
        for (let i = 0; i < 100; i++) {
          if (data[i] && data[i].leading_cause) {
            if (data[i].deaths >= 1000) {
              getColor();
              labels.push(data[i].leading_cause);
                death.value = {
                  labels: labels,
                  datasets: [
                    {
                      label: "Data" + i,
                      backgroundColor: colors,
                      data: chartData,
                    }
                  ]
                };
                chartData.push(data[i].deaths);
                
              }
            }
          }
          console.log(colors);
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
.place {
  align-items: center;
  border: 3px solid #2a3c75;
  padding: 3rem;
}
</style>