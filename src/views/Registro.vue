<template>
  <div>
    <h1 class="my-5">Registro de Usuarios</h1>
    <div class="alert alert-danger" v-if="error.tipo !== null">
      {{ error.mensaje }}
    </div>
    <form @submit.prevent="procesarFormulario">
      <input
        type="email"
        placeholder="correo"
        class="form-control my-2"
        v-model.trim="email"
        :class="[error.tipo === 'email' ? 'is-invalid' : '']"
      />
      <input
        type="password"
        placeholder="contraseña"
        class="form-control my-2"
        v-model="pass1"
      />
      <input
        type="password"
        placeholder="contraseña"
        class="form-control my-2"
        v-model="pass2"
        :class="passwords"
      />
      <p v-if="this.pass2 >1">Las contraseñas deben ser iguales y mayor a 5 caracteres</p>

      <button type="submit" class="btn btn-primary" :disabled="bloquear">
        Registrar
      </button>
    </form>
  </div>
</template>

<script>
import { mapActions, mapState } from "vuex";
export default {
  data() {
    return {
      email: "",
      pass1: "",
      pass2: "",
    };
  },
  computed: {
    ...mapState(["error"]),
    bloquear() {
      if (!this.email.includes("@")) {
        return true;
      }
      if (this.pass1.length > 5 && this.pass1 === this.pass2) {
        return false;
      }
      return true;
    },
    passwords() {
      if (this.pass2 > 1) {
        return this.pass1 === this.pass2 && this.pass1.length > 5
          ? "is-valid"
          : "is-invalid";
      }
    },
  },
  methods: {
    ...mapActions(["registrarUsuario"]),
    async procesarFormulario() {
      await this.registrarUsuario({ email: this.email, password: this.pass1 });
      if (this.error.tipo !== null) {
        return;
      }
      this.email = "";
      this.pass1 = "";
      this.pass2 = "";
    },
  },
};
</script>

