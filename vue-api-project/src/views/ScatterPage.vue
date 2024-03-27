<template>
  <div>
    <h1>Scatter Chart: Death Amounts vs. Death Rate</h1>
  </div>
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
  h1 {
  text-align: center;
  font-size: 22px;
  background-color: #a2b8e9;
  margin-top: 7rem;
  color: rgb(0, 33, 94);
}
  </style>