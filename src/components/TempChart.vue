<script>
  import {Line, mixins} from 'vue-chartjs'
  const { reactiveProp } = mixins
  export default Line.extend({
    mixins: [reactiveProp],
    mounted () {
      this.renderChart(this.chartData)
    }
  })
</script>
