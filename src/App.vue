<script setup>
import HeaderComponent from './components/HeaderComponent.vue';
import { RouterView } from 'vue-router'

</script>

<template>
  <div class="app">
    <HeaderComponent />
    <RouterView />
  </div>
  
</template>

<style scoped>

</style>
