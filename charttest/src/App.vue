<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Chart :chart-data="datacollection"/>
    <button @click="fillData()">Randomize</button>
  </div>
  
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
// import Chart from './components/Chart.vue'
// import axios from 'packs/axios'
import Chart from './chartbox'
// import chartbox from './chartbox'

export default {
    name: 'App',
    components: {
        // HelloWorld,
        Chart
    },
    data() {
            return {
                datacollection: null,
                videolength:null,
                labels: [],
                Percentages: [],
                data: [],
            }
    },
    mounted(){
        this.fillData()
    },
    methods: {
      fillData () {
        this.labels = []
        this.data = []
        this.videolength = this.getRandomIntforTime()
        for(var i=0;i<this.videolength;i += 30){
            this.labels.push(i)
        }
        for(var m=0;m<this.videolength-1;m++){
            this.Percentages.push(this.getRandomInt())
        }
        this.datacollection = {
            lineTension: 0,
            labels: this.labels,
            datasets: [{
                lineTension: 0,
                data: this.Percentages
            }]
        }
        // this.datacollection.labels = this.videolength
      },
      getRandomInt () {
        return Math.floor(Math.random() * 100)
      },
      getRandomIntforTime () {
        return Math.floor(Math.random() * 300)
      },
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
