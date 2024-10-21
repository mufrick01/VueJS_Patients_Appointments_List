import FormPatientAppointment from '@/components/FormPatientAppointment.vue';
<template>
    <form class="d-flex flex-column gap-2 p-4 justify-content-center" style="font-size: 15px;" @submit.prevent="SendForm">
        <h2 class="text-center mb-4" style="font-size: 40px;">Add Patient Appointment</h2>
        <label class="row">
            <span class="col-4 text-start" :class="{'text-danger':(formPatientAppointment.name.trim()==='')}">Name</span>
            <input type="text" class="col-8" v-model="formPatientAppointment.name" required>
        </label>
        <label class="row">
            <span class="col-4 text-start" :class="{'text-danger':(formPatientAppointment.date==='')}" >Date</span>
            <input type="date" class="col-8" v-model="formPatientAppointment.date" required>
        </label>
        <label class="row">
            <span class="col-4 text-start" :class="{'text-danger':(formPatientAppointment.time==='')}" >Time</span>
            <input type="time" class="col-8" v-model="formPatientAppointment.time" required>
        </label>
        <label class="row">
            <span class="col-4 text-start" :class="{'text-danger':(formPatientAppointment.severity==='')}">Severity</span>
            <select class="col-8" v-model="formPatientAppointment.severity" required >
                <option v-for="( { type, color }, index) in caseSeverity" :key="index" :value="color">
                    {{ type }}
                </option>
            </select>
        </label>
        <label class="row">
            <span class="col-4 text-start" :class="{'text-danger':(formPatientAppointment.notes.trim()==='')}" >Notes</span>
            <textarea maxlength="150" class="col-8" v-model="formPatientAppointment.notes" required></textarea>
        </label>
        <button type="submit" class="btn btn-warning col-4 ms-auto" :class="{'disabled':(isDisabled())}" >ADD</button>
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
                    color: '#00f'
                }
            ],

            formPatientAppointment: {
                name: '',
                date: '',
                time: '',
                severity: '',
                notes: '',
            }
            // formPatientAppointment: {
            //     name: 'Jhon doe',
            //     date: '1999-01-01',
            //     time: '02:02',
            //     severity: '#f00',
            //     notes: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniamet',
            // }
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

            this.resetForm();
        },

        resetForm(){
            this.formPatientAppointment.name='';
            this.formPatientAppointment.date='';
            this.formPatientAppointment.time='';
            this.formPatientAppointment.severity='';
            this.formPatientAppointment.notes='';
        },
        
        isDisabled(){
            if(this.formPatientAppointment.name.trim()==='') return true
            if(this.formPatientAppointment.date==='') return true
            if(this.formPatientAppointment.time==='') return true
            if(this.formPatientAppointment.severity==='') return true
            if(this.formPatientAppointment.notes.trim()==='') return true

            return false;
        }
    }
};
</script>

<style scoped>
</style>
