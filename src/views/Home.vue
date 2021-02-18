<template>
  <div>
    <h1>Formularios Con VUE.js</h1>
    <p>
      Para probar esta aplicacion debes ingresar los datos, quedan guardados en
      localStorage y no en base de datos
    </p>
    <form @submit.prevent="procesarFormulario">
      <Input :tarea="tarea" />
    </form>
    <br />
    <ListaTarea />
  </div>
</template>

<script>
import Input from "@/components/Input";
import ListaTarea from "@/components/ListaTarea";

import { mapActions } from "vuex";
const shortid = require("shortid");
export default {
  name: "Home",
  components: { Input, ListaTarea },
  data() {
    return {
      tarea: {
        id: "",
        nombre: "",
        categorias: [],
        estado: "",
        numero: 0,
      },
    };
  },
  methods: {
    ...mapActions(["setTareas", "cargarLocalStorage"]),
    procesarFormulario() {
      if (this.tarea.nombre.trim() === "") {
        console.log("Campo Vacio");
        return;
      }
      console.log("no esta vacio");
      //generar id
      this.tarea.id = shortid.generate();
      //enviar datos
      this.setTareas(this.tarea);
      //limpiar datos
      this.tarea = {
        id: "",
        nombre: "",
        categorias: [],
        estado: "",
        numero: 0,
      };
    },
  },
  created() {
    this.cargarLocalStorage();
  },
};
</script>
