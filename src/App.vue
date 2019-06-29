<template>
  <div id="app">
    <h1>{{nameApp}}</h1>
    <div class="container">
      <form v-on:submit.prevent="agregarTarea(tareas)">
        <input type="text" v-model="tareas.titulo">
        <button class="btn btn-primary" type="submit">Crear tarea</button>
      </form>
      <table class="table">
        <thead>
          <tr>
            <th>Hecho</th>
            <th>Tarea</th>
            <th>Eliminar</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="tarea in tareas" :class="{tareaHecha: tarea.hecho}">
            <td>
              <input type="checkbox" v-model="tarea.hecho">
            </td>
            <td>{{tarea.titulo}}</td>
            <td>
              <button class="btn btn-danger" v-on:click="eliminarTarea(tarea)">X</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "app",
  data: function() {
    return {
      nameApp: "Tareas Vue.js",
      tareas: [
        {
          titulo: "tarea 1",
          hecho: false
        },
        {
          titulo: "tarea 2",
          hecho: false
        },
        {
          titulo: "tarea 3",
          hecho: false
        }
      ]
    };
  },
  methods: {
    eliminarTarea: function(tarea) {
      this.tareas.splice(this.tareas.indexOf(tarea), 1);
    },
    agregarTarea: function(e) {
      this.tareas.push({
        titulo: this.tareas.titulo,
        hecho: false
      });
      this.tareas.titulo = "";
    }
  }
};
</script>

<style lang="scss">
@import "../node_modules/bootstrap/scss/bootstrap.scss";
.table {
  .tareaHecha {
    background: #ccc;
  }
}
</style>
