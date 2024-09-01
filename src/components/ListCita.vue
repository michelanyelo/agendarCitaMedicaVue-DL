<template>

    <h2 class="my-4">Mis Citas Médicas</h2>
    <div class="row">
        <div v-if="listaCitas.length > 0" class="row">
            <div v-for="(cita, idx) in listaCitas" :key="idx" class="col-md-4 mb-4">
                <div class="card rounded" :class="getCardClass(cita.gravedad)">
                    <div class="card-body">
                        <h5 class="card-title">{{ cita.paciente }}</h5>
                        <h6 class="card-subtitle mb-2 text-muted">Fecha: {{ cita.fecha }}</h6>
                        <p class="card-text">Hora: {{ cita.horario }}</p>
                        <p class="card-text">Motivo: {{ cita.motivo }}</p>
                        <button class="btn btn-danger btn-sm mt-3" @click="enviarId(cita.id)"
                            aria-label="Eliminar cita">
                            <i class="bi bi-trash"></i> Eliminar
                        </button>
                    </div>
                </div>
            </div>
        </div>
        <p v-else class="text-danger text-center">Aún no hay citas registradas</p>
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
        enviarId(id) {
            this.$emit('eliminar-cita', id)
        },
        getCardClass(gravedad) {
            switch (gravedad) {
                case 1: return 'bg-success bg-opacity-25';
                case 2: return 'bg-warning bg-opacity-25';
                case 3: return 'bg-danger bg-opacity-25';
                default: return '';
            }
        }
    },
};
</script>

<style scoped>
h2 {
    font-size: 1.75rem;
    color: #343a40;
}

.card {
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.card-title {
    font-size: 1.25rem;
    color: #495057;
}

.card-subtitle {
    font-size: 0.9rem;
    color: #6c757d;
}

.card-text {
    font-size: 0.9rem;
    color: #343a40;
}
</style>
