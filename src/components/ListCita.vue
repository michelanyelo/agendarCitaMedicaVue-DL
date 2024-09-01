<template>
    <div class="container">
        <h2 class="mt-5">Mis Citas Médicas</h2>
        <div class="row">
            <div v-if="listaCitas.length > 0" class="col-12">
                <div v-for="(cita, idx) in listaCitas" :key="idx" class="col-md-4 mb-3">
                    <div class="card" :class="{
                        'bg-success bg-opacity-25': cita.gravedad === 1,
                        'bg-warning bg-opacity-25': cita.gravedad === 2,
                        'bg-danger bg-opacity-25': cita.gravedad === 3
                    }">
                        <div class="card-body">
                            <h5 class="card-title">Paciente: {{ cita.paciente }}</h5>
                            <h6 class="card-subtitle mb-2 text-muted">Fecha de Atención: {{ cita.fecha }}</h6>
                            <p class="card-text">Hora de Atención: {{ cita.horario }}</p>
                            <p class="card-text">Motivo de Consulta: {{ cita.motivo }}</p>
                            <button class="btn btn-danger btn-sm">
                                <i class="bi bi-trash"></i> Eliminar
                            </button>
                        </div>
                    </div>
                </div>
            </div>
            <p v-else class="text-danger">Aún no hay citas registradas</p>
        </div>
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
