<template>
    <div class="historial-table">
      <h2>Historial de Ingresos/Gastos</h2>
      <table>
        <thead>
          <tr>
            <th>Tipo</th>
            <th>Monto</th>
            <th>Descripción</th>
            <th>Fecha</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="registro in registros" :key="registro.id">
            <td>{{ registro.tipo }}</td>
            <td>{{ registro.monto }}</td>
            <td>{{ registro.descripcion }}</td>
            <td>{{ registro.fecha }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    props: ['registros']
  };
  </script>
  
  <style scoped>
  .historial-table {
    max-width: 800px;
    margin: 20px auto;
  }
  table {
    width: 100%;
    border-collapse: collapse;
  }
  th, td {
    padding: 10px;
    text-align: left;
    border-bottom: 1px solid #ddd;
  }
  th {
    background-color: #f2f2f2;
  }
  </style>
  