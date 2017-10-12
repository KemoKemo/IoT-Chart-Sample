<template>
  <div>
    <temp-chart :width="900" :height="300" :chartData="chartData"></temp-chart>
    <button @click="fillData">Update by DB dataset</button>
  </div>
</template>

<script>
// TODO: Please change for your environment.
const dbURI = 'http://192.168.26.101:9000/sensors'

import TempChart from './components/TempChart.vue'
import Axios from 'axios'
export default {
  components: {
    TempChart
  },
  data() {
    return {
      chartData: {},
      datasets: []
    }
  },
  methods: {
    fillData () {
      Axios.get(dbURI).then(response => {
                this.datasets = response.data.data_set_list;
                let dateArray = [];
                let valueArray = [];
                for (var i = 0; i < this.datasets.length; i++) {
                  dateArray.push(this.datasets[i].date)
                  valueArray.push(this.datasets[i].sensor_list[0].temp_c)
                }
                this.chartData = {
                  labels: dateArray,
                  datasets: [
                    {
                      label: 'Temperature Chart',
                      fill: false,
                      backgroundColor: '#1347cc',
                      data: valueArray
                    }
                  ],
                }
            }, response => {
                this.message = 'Failed to get data.';
            });
    }
  },
  created() {
    this.fillData()
  }
}
</script>
