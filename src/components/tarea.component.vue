<template>
  <div class="row" @mouseenter="focoTarea = true" @mouseleave="focoTarea = false">
    <div class="col">
      <div class="tarea-item">
        <input class="form-check-input" type="checkbox" v-model="tarea.finalizada" />
        <span class="text-primary" :class="{tachado: tarea.finalizada}">{{tarea.texto}}</span>
        <button v-if="focoTarea" @click="onEliminar" class="ml-2 btn btn-danger btn-sm">x</button>
      </div>
    </div>
  </div>
</template>
<script>
import Tarea from "../model/tarea";
export default {
  name: "TareaComponent",
  props: {
    tarea: Tarea
  },
  data() {
    return {
      focoTarea: false
    };
  },
  methods: {
    onEliminar() {
      this.$emit("eliminar");
    }
  }
};
</script>
<style scoped>
.tachado {
  text-decoration: line-through;
}

.tarea-item span {
  font-size: x-large;
}
</style>