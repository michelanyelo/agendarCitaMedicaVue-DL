<template>
    <h2 class="mt-5">Mi Formulario</h2>
    <form class="row g-3 w-50 mx-auto" @submit.prevent="registrarCita">
        <div class="col-12">
            <label for="inputPaciente" class="form-label"
                :class="{ 'text-danger fw-bold': !cita.paciente.trim() }">Nombre completo del
                paciente</label>
            <input type="text" class="form-control" id="inputPaciente" v-model="cita.paciente">
        </div>
        <div class="col-md-6">
            <label for="inputFecha" class="form-label"
                :class="{ 'text-danger fw-bold': !cita.fecha.trim() }">Fecha</label>
            <input type="date" class="form-control" id="inputFecha" v-model="cita.fecha">
        </div>
        <div class="col-md-6">
            <label for="inputHora" class="form-label"
                :class="{ 'text-danger fw-bold': !cita.horario.trim() }">Hora</label>
            <input type="time" class="form-control" id="inputHora" v-model="cita.horario">
        </div>
        <div class="col-md-6">
            <label for="inputGravedad" class="form-label"
                :class="{ 'text-danger fw-bold': cita.gravedad <= 0 }">Gravedad</label>
            <select id="inputGravedad" class="form-select" v-model="cita.gravedad">
                <option value="" disabled>Elije una opción...</option>
                <option v-for="(nivel, idx) in nivelGravedad" :key="idx" :value="idx + 1">{{ nivel }}</option>
            </select>
        </div>
        <div class="col-md-6">
            <label for="inputMotivo" class="form-label"
                :class="{ 'text-danger fw-bold': !cita.motivo.trim() }">Motivo</label>
            <textarea rows="1" class="form-control" id="inputMotivo" placeholder="Detalle el motivo de la cita"
                v-model="cita.motivo"></textarea>
        </div>
        <div class="col-12">
            <button type="submit" class="btn btn-success" :disabled="!isFormValid">Agregar cita</button>
        </div>
    </form>
</template>

<script>
export default {
    name: 'FormCita',
    emits: ['submit-cita'],
    data() {
        return {
            nivelGravedad: ['Baja', 'Media', 'Alta'],
            cita: {
                id: new Date().getTime(),
                paciente: '',
                fecha: '',
                horario: '',
                gravedad: '',
                motivo: '',
            }
        };
    },
    computed: {
        isFormValid() {
            return this.cita.paciente.trim() !== '' &&
                this.cita.fecha.trim() !== '' &&
                this.cita.horario.trim() !== '' &&
                this.cita.gravedad > 0 &&
                this.cita.motivo.trim() !== '';
        }
    },
    methods: {
        registrarCita() {
            if (!this.isFormValid) return;
            this.$emit('submit-cita', this.cita)
            this.cita = {
                id: new Date().getTime(),
                paciente: '',
                fecha: '',
                horario: '',
                gravedad: '',
                motivo: '',
            };
        }
    },
};
</script>
<style scoped></style>
