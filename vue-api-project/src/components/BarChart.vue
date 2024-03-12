<template>
<div class="container">
    <Bar v-if="loaded" :data="chartData" />
  </div>
</template>

<script>
import {ref, onMounted } from "vue"
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

async function getDeaths(){
  try{
  let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json")
  let data = await get.json();
  console.log(data)
  return data
  } catch(error){
    console.log(error)
  }
}

onMounted(() => {
  getDeaths();
});

export default {
  name: 'BarChart',
  components: { Bar },
  props: {
    death: String,
    year: Number
  },
  data: () => ({
    loaded: false,
    chartData: null
  }),
  setup(props){
    console.log(props.death)
  },

  data: () => ({
    loaded: false,
    chartData: null
  }),
  async mounted () {
    this.loaded = false

    try {
      const { userlist } = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json")
      this.chartdata = userlist

      this.loaded = true
    } catch (e) {
      console.error(e)
    }
  }
}
</script>

<style scoped>

</style>