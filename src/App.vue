<template>
  <div>
    <NavBar />
  </div>
  <div class="container">
    <router-view />
  </div>
</template>
<script>
import { mapActions } from 'vuex'
import NavBar from "@/components/NavBar";
export default {
  components: {
    NavBar,
  },
  methods:{
    ...mapActions(['cargarLocalStorage'])
  },
  created(){
    this.cargarLocalStorage()
  }
};
</script>
<style>
</style>
