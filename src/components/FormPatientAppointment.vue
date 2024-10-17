import FormPatientAppointment from '@/components/FormPatientAppointment.vue';
<template>
    <form class="d-flex flex-column gap-2 container p-5 justify-content-center" style="font-size: 15px;" @submit.prevent="SendForm">
        <h2 class="text-center mb-4" style="font-size: 50px;">Add Patient Appointment</h2>
        <label class="row">
            <span class="col-4 text-start">Name</span>
            <input type="text" class="col-8" v-model="formPatientAppointment.name">
        </label>
        <label class="row">
            <span class="col-4 text-start">Date</span>
            <input type="date" class="col-8" v-model="formPatientAppointment.date">
        </label>
        <label class="row">
            <span class="col-4 text-start">Time</span>
            <input type="time" class="col-8" v-model="formPatientAppointment.time">
        </label>
        <label class="row">
            <span class="col-4 text-start">Severity</span>
            <select class="col-8" v-model="formPatientAppointment.severity">
                <option v-for="( { type, color }, index) in caseSeverity" :key="index" :value="color">
                    {{ type }}
                </option>
            </select>
        </label>
        <label class="row">
            <span class="col-4 text-start">Notes</span>
            <textarea class="col-8" v-model="formPatientAppointment.notes"></textarea>
        </label>
        <button type="submit" class="btn btn-primary col-4 ms-auto">ADD</button>
    </form>
</template>

<script>
export default {
    name: 'FormPatientAppointment',
    data() {
        return {
            caseSeverity: [
                {
                    type: 'Emergent',
                    color: '#f00'
                },
                {
                    type: 'Urgent',
                    color: '#ff0'
                },
                {
                    type: 'Non-Urgent',
                    color: '#f00'
                }
            ],

            formPatientAppointment: {
                name: '',
                date: '',
                time: '',
                severity: '',
                notes: '',
            }
        };
    },
    methods: {
        SendForm() {
            this.$emit('form-sent',
                {
                    id: Date.now(),
                    ...this.formPatientAppointment
                }
            )
        }
    }
};
</script>

<style scoped>
/* Estilos aquí */
</style>
