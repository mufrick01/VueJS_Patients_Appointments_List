<template>
    <div :style="{ backgroundColor: severity }" class="d-flex flex-column p-3" style="border: 10px solid #333">
      <h6 class="fw-bold">Nombre</h6>
      <h4 class="fw-bold text-capitalize bg-light p-2">{{ name }}</h4>
      <h6>{{ time }} | {{ date }}</h6>
      <h5 class="fw-bold">Notes</h5>
      <p class="bg-light p-2">{{ notes }}</p>
      <button class="mt-auto p-1 fw-bolder text-capitalize btn btn-danger" style="border: #222 solid 2px; font-size: 30px;" @click="clickDeleteButton">delete</button>
    </div>
</template>

<script>
export default {
  name: 'CardPatientAppointment',
  props: {
    patient: {
      type: Object,
      required: true,
    }
  },
  data(){
    const {id,name,date,time,severity,notes} = this.patient
    return {id,name,date,time,severity,notes}
  },
  methods:{
    clickDeleteButton(){
      this.$emit('click-delete',this.patient)
    }
  }
};
</script>

<style scoped>
/* Estilos aquí */
</style>
