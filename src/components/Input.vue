<template>
  <div>
    <input
      type="text"
      class="form-control my-2"
      placeholder="Ingrese nombre"
      v-model.trim="tarea.nombre"
    />
    <div class="form-check form-check-inline">
      <input
        type="checkbox"
        id="check-1"
        class="form-check-input"
        v-model="tarea.categorias"
        value="JavaScript"
      />
      <label for="check-1" class="form-check-label">JavaScript</label>
    </div>
    <div class="form-check form-check-inline">
      <input
        type="checkbox"
        id="check-2"
        class="form-check-input"
        v-model="tarea.categorias"
        value="Node.js"
      />
      <label for="check-2" class="form-check-label">Node.js</label>
    </div>

    <div class="mt-2">
      <div class="form-check form-check-inline">
        <input
          type="radio"
          id="radio-1"
          class="form-check-input"
          value="urgente"
          v-model="tarea.estado"
        />
        <label for="radio-1" class="form-check-label">Urgente</label>
      </div>

      <div class="form-check form-check-inline">
        <input
          type="radio"
          id="radio-2"
          class="form-check-input"
          value="relax"
          v-model="tarea.estado"
        />
        <label for="radio-2" class="form-check-label">Relax</label>
      </div>
    </div>

    <div class="mt-">
      <input type="number" v-model.number="tarea.numero" class="form-control" />
    </div>
    <button
      class="btn btn-dark mt-2 btn-block"
      type="submit"
      :disabled="validar"
    >
      Procesar
    </button>
  </div>
</template>
<script>
export default {
  props: {
    tarea: Object,
  },
  computed: {
    validar() {
      return this.tarea.nombre.trim() === "" ? true : false;
    },
  },
};
</script>