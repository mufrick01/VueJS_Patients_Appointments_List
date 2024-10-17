<template>
  <div id="app" class="bg-dark text-white">
    <MainPage class="mainPage"/>
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

.mainPage{
  background-color: #333;
  min-height: 100vh;
  max-width: 100vw;
}

</style>
