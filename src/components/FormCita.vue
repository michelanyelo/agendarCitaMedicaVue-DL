<template>
    <form class="row g-3 w-50 mx-auto" @submit.prevent="registrarConsulta">
        <div class="col-12">
            <label for="inputPaciente" class="form-label"
                :class="{ 'text-danger fw-bold': consulta.paciente.trim() == 0 }">Nombre completo del
                paciente</label>
            <input type="text" class="form-control" id="inputPaciente" v-model="consulta.paciente">
        </div>
        <div class="col-md-6">
            <label for="inputFecha" class="form-label"
                :class="{ 'text-danger fw-bold': consulta.fecha.trim() == 0 }">Fecha</label>
            <input type="date" class="form-control" id="inputFecha" v-model="consulta.fecha">
        </div>
        <div class="col-md-6">
            <label for="inputHora" class="form-label"
                :class="{ 'text-danger fw-bold': consulta.horario.trim() == 0 }">Hora</label>
            <input type="time" class="form-control" id="inputHora" v-model="consulta.horario">
        </div>
        <div class="col-md-6">
            <label for="inputGravedad" class="form-label"
                :class="{ 'text-danger fw-bold': consulta.gravedad <= 0 }">Gravedad</label>
            <select id="inputGravedad" class="form-select" v-model="consulta.gravedad">
                <option value="" disabled>Elije una opción...</option>
                <option v-for="(nivel, idx) in nivelGravedad" :key="idx" :value="idx + 1">{{ nivel }}</option>
            </select>
        </div>
        <div class="col-md-6">
            <label for="inputMotivo" class="form-label"
                :class="{ 'text-danger fw-bold': consulta.motivo.trim() == 0 }">Motivo</label>
            <textarea rows="1" class="form-control" id="inputMotivo" placeholder="Detalle el motivo de la consulta"
                v-model="consulta.motivo"></textarea>
        </div>
        <div class="col-12">
            <button type="submit" class="btn btn-success" :disabled="!isFormValid">Agregar Consulta</button>
        </div>
    </form>
</template>

<script>
export default {
    name: 'FormCita',
    data() {
        return {
            nivelGravedad: ['Baja', 'Media', 'Alta'],
            consulta: {
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
            return this.consulta.paciente.trim() !== '' &&
                this.consulta.fecha.trim() !== '' &&
                this.consulta.horario.trim() !== '' &&
                this.consulta.gravedad > 0 &&
                this.consulta.motivo.trim() !== '';
        }
    },
    methods: {
        registrarConsulta() {
            if (!this.isFormValid) return;
            this.$emit('submit-cita', this.consulta)
            this.consulta = {
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
