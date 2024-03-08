<template>
  <div>
         <apiChart />
  </div>
</template>

<script>
import { ref } from "vue";
import apiChart from '@/components/apiChart.vue'

const dead = ref("");
async function getDead() {
  try {
    let res = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
    if (Response.status != 200) {
      throw new Error(response.statusText)
    }
    console.log(response);
    let data = await res.json();
    console.log(data);
  } catch (error) {
    console.log("Sorry, error.")
  }
  /* dead.value = data.results; */
}
getDead();
/* onMounted(() => {
  getDead();
}); */

export default {
  name: 'AboutView',
  components: { apiChart }
}
</script>

<style scoped>

</style>