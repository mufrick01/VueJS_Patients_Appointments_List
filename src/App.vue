<template>
  <div id="app" class="bg-dark text-white">
    <MainPage />
  </div>
</template>

<script>
import MainPage from './pages/MainPage.vue';


export default {
  name: 'App',
  components: {
    MainPage
  }
}
</script>

<style>
#app {}
</style>
