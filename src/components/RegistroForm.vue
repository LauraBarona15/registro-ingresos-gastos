<template>
  <div class="registro-form">
    <h2>Registro de Ingresos/Gastos</h2>
    <form @submit.prevent="agregarRegistro">
      <div>
        <label for="tipo">Tipo:</label>
        <select v-model="nuevoRegistro.tipo" required>
          <option value="ingreso">Ingreso</option>
          <option value="gasto">Gasto</option>
        </select>
      </div>
      <div>
        <label for="monto">Monto:</label>
        <input type="number" v-model="nuevoRegistro.monto" required />
      </div>
      <div>
        <label for="descripcion">Descripción:</label>
        <input type="text" v-model="nuevoRegistro.descripcion" required />
      </div>
      <button type="submit">Agregar</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      nuevoRegistro: {
        tipo: '',
        monto: '',
        descripcion: ''
      }
    };
  },
  methods: {
    agregarRegistro() {
      this.$emit('nuevo-registro', { ...this.nuevoRegistro });
      this.nuevoRegistro.tipo = '';
      this.nuevoRegistro.monto = '';
      this.nuevoRegistro.descripcion = '';
    }
  }
};
</script>

<style scoped>
.registro-form {
  max-width: 400px;
  margin: 0 auto;
  padding: 20px;
  border: 1px solid #ccc;
  border-radius: 5px;
}
label {
  display: block;
  margin-top: 10px;
}
input, select {
  width: 100%;
  padding: 8px;
  margin-top: 5px;
  box-sizing: border-box;
}
button {
  margin-top: 10px;
  padding: 10px;
  background-color: #4CAF50;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}
button:hover {
  background-color: #45a049;
}
</style>
