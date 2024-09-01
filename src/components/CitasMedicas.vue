<template>
    <!-- Formulario -->
    <FormCita @submit-cita="agregarCita" />
    <!-- Listado de Citas -->
    <ListCita :listaCitas="citas" @eliminar-cita="eliminarCita" />
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

<style scoped></style>
