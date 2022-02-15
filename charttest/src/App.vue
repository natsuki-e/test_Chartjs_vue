<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Chart :chart-data="datacollection" :options="options" style="width='400vh';height='300vh'"/>
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
                rand: 0
            }
    },
    mounted(){
        this.fillData()
    },
    methods: {
      fillData () {
        this.labels = []
        this.data = []
        this.rand = 0
        this.videolength = this.getRandomIntforTime()
        for(var i=0;i<this.videolength;i ++){
            this.labels.push(i)
        }
        for(var m=0;m<this.videolength;m++){
            if(m == 0) {
                this.rand = this.getRandomInt()
            }else if(this.getRandomInt() > 76){
                this.rand = this.rand - Math.floor(Math.random() * 5)
                if(this.rand <= 0) this.rand = 5
            }else{
                this.rand = this.rand + Math.floor(Math.random() * 5)
                if(this.rand >= 100) this.rand = 100
            }
            this.Percentages.push(this.rand)
        }
        this.datacollection = {
            lineTension: 0,
            labels: this.labels,
            datasets: [{
                borderColor: 'rgba(0,1,200,0.3)',
                pointRadius: 0,
                fill: false,
                lineTension: 0,
                data: this.Percentages
            }]
        }
        this.options ={
            responsive: true,
            legend: {
                display: false
            },
            scales: {
                xAxes: [
                    {
                        ticks:{
                            maxTicksLimit: 2
                        }
                    }
                ],
                yAxes: [{
                    ticks: {
                        min:0,
                        max: 100,
                        stepSize: 33
                    }
                }]
            },
            tooltips:{
                mode: 'nearest',
                axis: 'x',
                intersect: false
            }
        }
        // this.datacollection.labels = this.videolength
      },
      getRandomInt () {
        return Math.floor(Math.random() * 30) + 70
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
