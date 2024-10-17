<template>
  <div class="d-block d-md-flex">
    <FormPatientAppointment style="width: 400px;" class="h-vh"/>
    <div class="flex-grow-1 bg-white">
      asd
    </div>
  </div>
</template>

<script>
import FormPatientAppointment from '@/components/FormPatientAppointment.vue';

export default {
  name: 'MainPage',
  components: {
    FormPatientAppointment
  },
  data() {
    return {
    };
  },
};
</script>
<style scoped>
.h-vh{
  height: 100vh;
}
</style>
