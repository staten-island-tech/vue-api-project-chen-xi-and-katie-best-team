<template>
  <div>
    <BarChart />
  </div>
</template>

<script>
import {ref, onMounted } from "vue"
import BarChart from '@/components/BarChart.vue'

const deaths = ref("");
async function getDeaths(){
  let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json")
  let data = await get.json();
  deaths.value = data.results;
}

onMounted(() => {
  getDeaths();
});

export default {
  name: 'App',
  components: { BarChart }
}
</script>

<style scoped>

</style>