<script>
export default {
  props: {
    criterioNombre: {
      type: String,
      default: ''
    },
    criterioDni: {
      type: String,
      default: ''
    }
  },
  data() {
    return {
      personas: [
        { nombre: "Daniel", apellido: "Sanchez", correo: "danielsanchez68@hotmail.com", dni: "20442873" },
        { nombre: "Juan", apellido: "Perez", correo: "j@p.gmail.com", dni: "12345678" },
        { nombre: "Ana", apellido: "Suarez", correo: "a@s.gmail.com", dni: "87654321" },
        { nombre: "...", apellido: "...", correo: "...", dni: "..." }
      ]
    };
  },
  computed: {
    personasFiltradas() {
      return this.personas.filter((persona) => {
        let nombreCompleto = `${persona.nombre} ${persona.apellido}`;
        let dni = persona.dni;

        
        if (!this.criterioNombre && !this.criterioDni) return true;

     
        if ((this.criterioNombre.length > 0 && this.criterioNombre.length < 3) || 
            (this.criterioDni.length > 0 && this.criterioDni.length < 3)) {
          return false;
        }

        
        if (this.criterioNombre && !this.criterioDni) {
          return nombreCompleto.toLowerCase().includes(this.criterioNombre.trim().toLowerCase());
        }

        if (!this.criterioNombre && this.criterioDni) {
          return dni.includes(this.criterioDni);
        }

       
        return nombreCompleto.toLowerCase().includes(this.criterioNombre.trim().toLowerCase()) &&
               dni.includes(this.criterioDni);
      });
    }
  },
  methods: {
    getNombreCompleto(persona) {
      return `${persona.nombre} ${persona.apellido}`;
    }
  }
};
</script>

<template>
  <div class="card-deck m-0">
    <div class="row">
      <div class="col" v-for="persona in personasFiltradas" :key="persona.dni">
        <div class="card mb-3">
          <div class="card-body">
            <h5 class="card-title">{{ getNombreCompleto(persona) }}</h5>
            <p class="card-text">DNI: {{ persona.dni }}</p>
            <a href="#" class="card-link">{{ persona.correo }}</a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>

</style>