<template>
  <div id="app">
    <RegistroForm @nuevo-registro="agregarRegistro"></RegistroForm>
    <HistorialTable :registros="registros"></HistorialTable>
    <Grafica :datacollection="datacollection"></Grafica>
  </div>
</template>

<script>
import RegistroForm from './components/RegistroForm.vue'
import HistorialTable from './components/HistorialTable.vue'
import Grafica from './components/GraficaIngresosGastos.vue'

export default {
  components: {
    RegistroForm,
    HistorialTable,
    Grafica
  },
  data() {
    return {
      registros: [],
      datacollection: {
        labels: [],
        datasets: [
          {
            label: 'Ingresos',
            backgroundColor: '#4CAF50',
            data: []
          },
          {
            label: 'Gastos',
            backgroundColor: '#FF6384',
            data: []
          }
        ]
      }
    }
  },
  methods: {
    agregarRegistro(registro) {
      registro.id = Date.now();
      registro.fecha = new Date().toLocaleString();
      this.registros.push(registro);
      this.actualizarGrafica();
    },
    actualizarGrafica() {
      const ingresos = this.registros.filter(registro => registro.tipo === 'ingreso').reduce((total, registro) => total + parseFloat(registro.monto), 0);
      const gastos = this.registros.filter(registro => registro.tipo === 'gasto').reduce((total, registro) => total + parseFloat(registro.monto), 0);
      this.datacollection.labels = ['Ingresos', 'Gastos'];
      this.datacollection.datasets[0].data = [ingresos];
      this.datacollection.datasets[1].data = [gastos];
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
