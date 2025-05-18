<script>
import Binding from './components/Binding.vue';

export default {
  components: {
    Binding
  },
  data() {
    return {
      criterioDeBusqueda: ''
    };
  }
};
</script>

<template>
  <header>
    <div class="container-fluid mt-3">
      <input type="text" class="form-control" v-model="criterioDeBusqueda"
        placeholder="Ingresar un criterio de búsqueda..." />
      <br />
    </div>
  </header>

  <main>
    <Binding :criterioDeBusqueda="criterioDeBusqueda" />
  </main>
</template>

<style scoped>

</style>