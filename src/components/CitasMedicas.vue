<template>
    <!-- Formulario -->
    <FormCita @submit-cita="agregarConsulta" />
    <!-- Listado de Citas -->
    <ListCita :listaCitas="citas" />
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
        agregarConsulta(consulta) {
            this.citas.push(consulta);
        }
    }
};
</script>

<style scoped></style>
