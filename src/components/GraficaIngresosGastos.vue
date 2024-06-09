<template>
  <div class="grafica">
    <h2>Gráfica de Ingresos/Gastos</h2>
    <bar-chart :chart-data="datacollection"></bar-chart>
  </div>
</template>

<script>
import { Bar } from 'vue-chartjs'
import { Chart, registerables } from 'chart.js'
Chart.register(...registerables)

export default {
  components: {
    'bar-chart': {
      extends: Bar,
      props: ['chartData'],
      mounted() {
        this.renderChart(this.chartData, { responsive: true, maintainAspectRatio: false })
      }
    }
  },
  props: ['datacollection']
}
</script>

<style scoped>
.grafica {
  max-width: 800px;
  margin: 20px auto;
}
</style>
