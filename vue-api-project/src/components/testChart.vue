<template>
    <div class="container">
        <Bar v-if="loaded" :data="chartData"/> 
      </div>
    </template>
    
    <script>
    import { ref, onMounted } from "vue"
    import { Bar } from 'vue-chartjs'
    import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from 'chart.js'
    
    ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale)
    
    
    export default {
      name: "testChart",
      components: { Bar },
      data: () => ({
        loaded: false,
        death: null
      }),
    async getDeaths() {
      this.loaded === false;
      try {
        let get = await fetch("https://data.cityofnewyork.us/resource/jb7j-dtam.json");
        this.death = await get.json();
      
        console.log(death)
       this.loaded = true
      
      } catch (error) {
        console.log(error)
      }
    
    },
    onMounted(getDeaths){
      getDeaths()
    return{
      death,
      loaded
    }
      },
      chartOptions: {
      responsive: true,
      maintainAspectRatio: false
    }
    }
    
    
    </script>
    
    <style scoped>
    
    </style>