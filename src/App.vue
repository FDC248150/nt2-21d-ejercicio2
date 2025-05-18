<script>
import Binding from './components/Binding.vue';

export default {
  components: {
    Binding
  },
  data() {
    return {
      criterioNombre: '',
      criterioDni: ''
    };
  }
};
</script>

<template>
  <header>
    <div class="container-fluid mt-3">
      <input type="text" class="form-control" v-model="criterioNombre"
        placeholder="Buscar por nombre o apellido..." />
      <br />
      <input type="text" class="form-control" v-model="criterioDni"
        placeholder="Buscar por DNI..." />
      <br />

    
      <div v-if="(criterioNombre.length > 0 && criterioNombre.length < 3) || 
                  (criterioDni.length > 0 && criterioDni.length < 3)" 
           class="alert alert-warning">
        ⚠️ Debes ingresar al menos 3 caracteres en alguno de los filtros.
      </div>
    </div>
  </header>

  <main>
    <Binding :criterioNombre="criterioNombre" :criterioDni="criterioDni" />
  </main>
</template>

<style scoped>

</style>