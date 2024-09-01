<template>
    <div class="container py-5 px-5 rounded">
        <!-- Formulario -->
        <FormCita @submit-cita="agregarCita" />
        <!-- Listado de Citas -->
        <ListCita :listaCitas="citas" @eliminar-cita="eliminarCita" />
    </div>
</template>

<script>
import FormCita from './FormCita.vue'
import ListCita from './ListCita.vue'

export default {
    name: 'CitasMedicas',
    components: { FormCita, ListCita },
    data() {
        return {
            citas: []
        };
    },
    methods: {
        agregarCita(cita) {
            this.citas.push(cita);
        },
        eliminarCita(id) {
            this.citas = this.citas.filter(cita => cita.id !== id);
        }
    }
};
</script>

<style scoped>
.container {
    background: #ffffff;
    box-shadow: 0 4px 8px rgba(0, 0, 0, 0.1);
}
</style>
