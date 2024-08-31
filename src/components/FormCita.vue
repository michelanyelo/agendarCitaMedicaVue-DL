<template>
    <form class="row g-3 w-50 mx-auto">
        <div class="col-12">
            <label for="inputPaciente" class="form-label">Nombre completo del paciente</label>
            <input type="text" class="form-control" id="inputPaciente">
        </div>
        <div class="col-md-6">
            <label for="inputFecha" class="form-label">Fecha</label>
            <input type="date" class="form-control" id="inputFecha">
        </div>
        <div class="col-md-6">
            <label for="inputHora" class="form-label">Hora</label>
            <input type="time" class="form-control" id="inputHora">
        </div>
        <div class="col-md-6">
            <label for="inputGravedad" class="form-label">Gravedad</label>
            <select id="inputGravedad" class="form-select">
                <option selected>Elije una opción...</option>
            </select>
        </div>
        <div class="col-md-6">
            <label for="inputPaciente" class="form-label">Motivo</label>
            <textarea rows="1" class="form-control" id="inputPaciente"
                placeholder="Detalle el motivo de la consulta"></textarea>
        </div>
        <div class="col-12">
            <button type="submit" class="btn btn-primary">Sign in</button>
        </div>
    </form>
</template>

<script>
export default {
    name: 'FormCita',
    data() {
        return {

        };
    },
};
</script>
<style scoped></style>