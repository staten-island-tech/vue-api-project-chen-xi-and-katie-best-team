<template>
  <div>
    <BarChart/>
  </div>
</template>

<script>

import BarChart from '@/components/BarChart.vue'
import { ref, onMounted } from "vue"
const death = ref("")
async function getDeaths() {
  try {
    let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
    let data = await get.json();
    death.value = data.results
    console.log(death.value)
    return death
  } catch (error) {
    console.log(error)
  }
}

export default {
  name: 'App',
  components: { BarChart },
  data() {
    return death
  },
  onMounted() {
    getDeaths();
  },
}

</script>

<style scoped></style>