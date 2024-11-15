<template>
  <div @click="selectPlan" class="plan">
    <div class="description">
      <span class="title">{{ name }} {{ isSelected ? '🌟' : '' }}</span>
    </div>
  </div>
</template>

<script setup>
// Importamos la funcion para crear
// propiedad computada
import { computed } from 'vue'
// Usando un macro para
// definir props
//defineProps(['name','planIcon']);
const props = defineProps({
  name: {
    type: String,
    required: true
  },
  selectPlan: String
})
// Definiendo un evento
const emit = defineEmits(['select'])
// Funcion que permite cambiar el estado de la variables
//selected
const selectPlan = () => {
  // Emitir evento de que el
  // plan ha sido seleccionado
  emit('select', props.name)
}
// Creando una propiedad computada
// para saber si el plan ha sido seleccionado
const isSelected = computed(() => {
  return props.name === props.selectPlan
})
</script>

<style scoped></style>
