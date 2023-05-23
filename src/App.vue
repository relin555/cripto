<script setup>
import HeaderComponent from './components/HeaderComponent.vue';
import { RouterView } from 'vue-router'
import { ref, onMounted } from 'vue';

const shop = ref( [] );

onMounted( () =>
{
  fetch( 'https://fakestoreapi.com/products' )
    .then( res => res.json() )
    .then(json=> shop.value = json )
} );

</script>

<template>
  <div class="app">
    <HeaderComponent />
    <RouterView />
  </div>
  
</template>

<style scoped>

</style>
