<template>
  <div id="app">
    <h1>Productos</h1>
    <table border="1">
      <thead>
        <th>id</th>
        <th>nombre</th>
        <th>tipo</th>
        <th>descripcion</th>
        <th>valorUnidad</th>
        <th>fechaEntrega</th>
        <th>fechaVencimiento</th>
        <th>activo</th>
        <th>Accion</th>
      </thead>
      <tbody>
        <tr v-for="producto in productos" :key="producto.id">
          <td>{{ producto.id }}</td>
          <td>{{ producto.nombre }}</td>
          <td>{{ producto.tipo }}</td>
          <td>{{ producto.descripcion }}</td>
          <td>{{ producto.valorUnidad }}</td>
          <td>{{ producto.fechaEntrega }}</td>
          <td>{{ producto.fechaVencimiento }}</td>
          <td>{{ producto.activo }}</td>
          <td><button @click="elminarProducto(producto.id)">x</button></td>
        </tr>
      </tbody>
    </table>
    <button @click="fetchProductos">Recaragar</button>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data: () => ({
    productos: [],
  }),
  computed: {},
  methods: {
    fetchProductos: function() {
      axios
        .get("http://localhost:8000/contratos/productos/")
        .then((response) => {
          this.productos = response.data;
        })
        .catch((err) => {
          console.log(err);
        });
    },
    elminarProducto: function(id) {
      axios
        .delete("http://localhost:8000/contratos/productos/" + id + "/")
        .then(( ) => {})
        .catch((err) => {
          console.log(err);
        })
        .finally(() => {
          this.fetchProductos();
        });
    },
  },
  created: function() {},
  mounted: function() {
    this.fetchProductos();
  },
};
</script>

<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
