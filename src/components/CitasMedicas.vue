<template>
    <h1>Mi Formulario</h1>
    <FormCita @submit-cita="agregarConsulta" />
    <h1>Mis Citas Medicas</h1>
    <ul>
        <li v-for="(cita, index) in citas" :key="index">
            {{ cita.paciente }} - {{ cita.fecha }} - {{ cita.horario }} - {{ cita.gravedad }} - {{ cita.motivo }}
        </li>
    </ul>
</template>

<script>
import FormCita from './FormCita.vue'

export default {
    name: 'CitasMedicas',
    components: { FormCita },
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
