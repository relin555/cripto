<script setup>
import { defineProps } from 'vue';
defineProps( [ 'modelValue' ] );
defineEmits( [ 'update:modelValue' ] );
</script>

<template>
  <input 
    :value="modelValue" 
    @input="$emit('update:modelValue', $event.target.value)"
    type="text">
</template>