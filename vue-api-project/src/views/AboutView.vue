<template>
  <div>
    <apiChart />
  </div>
</template>

<script>
import apiChart from '@/components/apiChart.vue'

export default {
  name: 'App2',
  components: { apiChart }
}

import { ref, onMounted } from "vue";
const dead = ref("");
async function getDead() {
  let res = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
  let data = await res.json();
  dead.value = data.results;
}

onMounted(() => {
  getDead();
})
</script>

<style scoped>

</style>