<template>
    <div class="container">
        <h2 class="mt-5">Mis Citas Médicas</h2>
        <ul class="list-group" v-if="listaCitas.length > 0">
            <li v-for="(cita, idx) in listaCitas" :key="idx" class="list-group-item">
                {{ cita.paciente }} - {{ cita.fecha }} - {{ cita.horario }} - {{ cita.gravedad }} - {{ cita.motivo }}
            </li>
        </ul>
        <p v-else class="text-danger">Aún no hay citas registradas</p>
    </div>
</template>


<script>
export default {
    name: 'ListCita',
    props: {
        listaCitas: Array
    },
};
</script>
<style scoped></style>