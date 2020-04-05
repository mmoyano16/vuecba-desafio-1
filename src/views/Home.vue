<template>
  <div class="container">
    <!-- titulo -->
    <div class="row pt-5">
      <div class="col">
        <h1 class="display-3">Mis tareas</h1>
      </div>
    </div>

    <!-- input -->
    <div class="row">
      <div class="col">
        <form @submit.prevent="agregarTarea">
          <div class="form-group">
            <div class="input-group">
              <input
                v-model="tarea"
                class="form-control"
                placeholder="¿Tienes algo para hacer?"
                type="text"
                name="tarea"
                id="tarea"
              />
              <div class="input-group-append">
                <button type="submit" class="btn-primary">Agregar</button>
              </div>
            </div>
          </div>
        </form>
      </div>
    </div>

    <!-- lista -->
    <div class="row p-5">
      <div class="col">
        <div v-for="(tarea, i) in tareas" :key="i">
          <TareaComponent @eliminar="eliminarTarea(i)" class="mb-3" :tarea="tarea"></TareaComponent>
        </div>
      </div>
    </div>

    <!-- debug -->
    <!-- <div class="row">
      <div class="col">{{tarea}}</div>
    </div>-->
  </div>
</template>

<script>
import Tarea from "../model/tarea";
import TareaComponent from "../components/tarea.component";

export default {
  name: "Home",
  components: {
    TareaComponent
  },
  data() {
    return {
      tareas: [],
      tarea: ""
    };
  },
  methods: {
    agregarTarea() {
      if (this.tarea !== "") {
        this.tareas.push(new Tarea(this.tarea));
        this.tarea = "";
      }
    },
    eliminarTarea(i) {
      this.tareas.splice(i, 1);
    }
  }
};
</script>
