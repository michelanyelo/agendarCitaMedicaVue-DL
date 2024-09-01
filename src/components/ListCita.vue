<template>
    <div class="container">
        <h2 class="mt-5">Mis Citas Médicas</h2>
        <div class="row">
            <div v-if="listaCitas.length > 0" class="row">
                <div v-for="(cita, idx) in listaCitas" :key="idx" class="col-md-4 mb-3">
                    <div class="card" :class="getCardClass(cita.gravedad)">
                        <div class="card-body">
                            <h5 class="card-title">Paciente: {{ cita.paciente }}</h5>
                            <h6 class="card-subtitle text-muted">Fecha de Atención: {{ cita.fecha }}</h6>
                            <p class="card-text m-0 p-0">Hora de Atención: {{ cita.horario }}</p>
                            <p class="card-text m-0 p-0">Motivo de Consulta: {{ cita.motivo }}</p>
                            <button class="btn btn-danger btn-sm mt-3" @click="confirmarEliminacion(cita.id)"
                                aria-label="Eliminar cita">
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
        listaCitas: Array,
    },
    emits: ['eliminar-cita'],
    methods: {
        confirmarEliminacion(id) {
            if (confirm('¿Estás seguro de que quieres eliminar esta cita?')) {
                this.$emit('eliminar-cita', id);
            }
        },
        getCardClass(gravedad) {
            return {
                'bg-success bg-opacity-25': gravedad === 1,
                'bg-warning bg-opacity-25': gravedad === 2,
                'bg-danger bg-opacity-25': gravedad === 3
            };
        }
    }
};
</script>

<style scoped></style>
