<template>
  <div>
    <BarChart />
  </div>
</template>

<script>
import {ref, onMounted } from "vue"
import BarChart from '@/components/BarChart.vue'

const deaths = ref("");
const loading = ref(true);

async function getDeaths(){
  try{
  let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json")
  let data = await get.json();
  deaths.value = data.results;
  loading.value = false;
  console.log(deaths.value)
  } catch(error){
    console.log(error)
  }
}

onMounted(() => {
  getDeaths();
});

export default {
  name: 'App',
  components: { BarChart },
  functions: { onMounted }
}


</script>

<style scoped>

</style>