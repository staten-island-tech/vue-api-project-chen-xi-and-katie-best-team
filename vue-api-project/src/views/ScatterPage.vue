<template>
  <div>
      <scatterChart />
    </div>
  </template>
  
  <script>
  import scatterChart from '@/components/scatterChart.vue'
  
  
  export default {
    name: 'App',
    components: {
      scatterChart
    },
  }
  
  </script>
  
  <style scoped>
  div {
    width: 100%;
  }
  </style>