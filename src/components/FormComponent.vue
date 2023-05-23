<script setup>
import MyInput from '@/components/UI/MyInput.vue';
import { ref, watch } from 'vue'

const btcValue = ref( '' );

const emit = defineEmits( [ 'getValueBtc' ] );

watch( btcValue, () =>
{
  emit( 'getValueBtc', btcValue )
} );


</script>

<template>
  <form>
    <MyInput v-model="btcValue"/>
  </form>
</template>