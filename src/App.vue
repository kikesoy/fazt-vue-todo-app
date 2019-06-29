<template>
  <div id="app">
    <div class="container">
      <h1 class="mb-3">{{nameApp}}</h1>
      <form v-on:submit.prevent="agregarTarea(tareas)">
        <div class="input-group bg-dark mb-3 p-3">
          <input class="form-control" type="text" v-model="tareas.titulo" />
          <div class="input-group-append">
            <button class="btn btn-primary" type="submit">Crear tarea</button>
          </div>
        </div>
      </form>
      <table class="table">
        <thead>
          <tr>
            <th class="task-done">Hecho</th>
            <th class="task-title">Tarea</th>
            <th class="task-delete">Eliminar</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="tarea in tareas" :class="{tareaHecha: tarea.hecho}" v-bind:key="tarea.id">
            <td class="text-center">
              <input class="form-check-input" type="checkbox" v-model="tarea.hecho" />
            </td>
            <td>{{tarea.titulo}}</td>
            <td class="text-center">
              <button class="btn btn-danger" v-on:click="eliminarTarea(tarea)">X</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script>
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
    agregarTarea: function() {
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
  .task-done,
  .task-delete {
    width: 1%;
  }
  .tareaHecha {
    background: #ccc;
  }
}
</style>
