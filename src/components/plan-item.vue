<template>
  <div class="plan">
    <div class="description">
      <span class="title"> {{ planIcon }} {{ name }} </span>
    </div>
  </div>
</template>

<script setup>
// Usando un macro para
// definir props
defineProps(['name','planIcon']);
</script>

<style scoped></style>
