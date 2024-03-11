<template>
<div class="container">
    <Bar v-if="loaded" :mounted="userlist" />
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'

ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)

export default {
  name: 'BarChart',
  components: { Bar },
  props: {
    death: String,
    year: Number
  },
  setup(props){
    console.log(props.test)
  },

  async mounted () {

    this.loaded = false

    try {
      const { userlist } = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json")
      this.chartdata = userlist

      this.loaded = true
      console.log(this.death)
    } catch (e) {
      console.error(e)
    }
  }
}
</script>

<style scoped>

</style>