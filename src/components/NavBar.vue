<template>
  <div class="navbar navbar-dark bg-dark">
    <router-link to="/" class="navbar-brand">Formularios</router-link>
    <div class="d-flex">
      <router-link class="btn btn-dark" v-if="usuarioAutenticado" to="/"
        >Tareas</router-link
      >

      <router-link class="btn btn-dark" v-if="!usuarioAutenticado" to="/ingreso"
        >Ingresar</router-link
      >

      <router-link
        class="btn btn-dark"
        v-if="!usuarioAutenticado"
        to="/registro"
        >Registrarse</router-link
      >

      <button class="btn btn-dark" v-if="usuarioAutenticado" @click="cerrarSesion">
        Cerrar Sesión
      </button>
    </div>
  </div>
</template>
<script>
import { mapActions, mapGetters } from "vuex";
export default {
  computed: {
    ...mapGetters(["usuarioAutenticado"]),
  },
  methods:{
      ...mapActions(['cerrarSesion'])
  }
};
</script>