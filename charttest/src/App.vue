<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <Chart :chartdata="chartItems" :options="chartOptions"/>
  </div>
  
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import Chart from './chartbox'

export default {
  name: 'App',
  components: {
    HelloWorld,
    Chart
  },
  data() {
    return {
      chartItems: {
          labels: ["12月", "1月", "2月", "3月", "4月", "5月", "6月", "7月", "8月", "9月", "10月", "11月"],
          datasets: [{
            label: "月ごとの点数",
            data: [95, 70, 80, 65, 69, 80, 100, 100, 72, 81, 45, 70],
            backgroundColor: 'lightblue'
          }]
      },
      // 後程オプションを記述
      chartOptions: {
        maintainAspectRatio: false,
        scales: {
          xAxes: [{
            display: true,
            // X軸グリッド非表示
            gridLines: {
              display:false
            }
          }],
          // Y軸
          yAxes: [{
            display: true,
            position: 'right',
            ticks: {
              // 0から始まる
              beginAtZero: true,
              // 最大5目盛
              maxTicksLimit: 5,
            },
          }]
        },
      },
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
