<template>
  <section class="h-100 row">
    <article class="col-12 col-lg-4 bg-dark">
      <FormPatientAppointment class="mx-auto" @form-sent="formHandler" />
    </article>
    <article class="col-12 col-lg-8 d-flex flex-column">
      <h2 class="text-center text-capitalize mt-4">Appointments List</h2>
      <hr>
      <div class="d-flex flex-wrap justify-content-center">
        <CardPatientAppointment v-for="(patient) in patientsAppointments" :key="patient.id" :patient="patient"
        class="text-dark" style="width: 300px;"/>
      </div>
    </article>
  </section>
</template>

<script>
import CardPatientAppointment from '@/components/CardPatientAppointment.vue';
import FormPatientAppointment from '@/components/FormPatientAppointment.vue';

export default {
  name: 'MainPage',
  components: {
    FormPatientAppointment,
    CardPatientAppointment
  },
  data() {
    return {
      patientsAppointments: []
    };
  },
  methods: {
    formHandler(formData) {
      this.patientsAppointments.push(formData)
    }
  }
};
</script>
<style scoped>
.h-vh {
  /* height: 100vh; */
}
</style>
