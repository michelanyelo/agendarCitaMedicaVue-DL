<template>
    <h1>Mi Formulario</h1>
    <FormCita />
    <h1>Mis Citas Medicas</h1>
</template>

<script>
import FormCita from './FormCita.vue'
export default {
    name: 'CitasMedicas',
    components: { FormCita },
    data() {
        return {

        };
    },
};
</script>
<style scoped></style>