<script setup>
import { ref } from 'vue';

// ---- Modelo ----
const header = ref('App lista de compras');
const newItem = ref('');
const newItemHighPriority = ref(false);
const editing = ref(true);

// ---- Items ----
const items = ref([
  { id: '0', label: '10 Bolillos' },
  { id: '1', label: '1 Lata Frijoles' },
  { id: '2', label: '1 Chelas' },
  { id: '3', label: '1 Nutella' },
]);

// ---- Métodos ----
const saveItem = () => {
  // Redirigir a Google si la caja de texto está vacía
  if (newItem.value.trim() === '') {
    window.location.href = 'https://www.google.com';
    return;
  }
  
  // Agregar nuevo item
  items.value.push({ id: String(items.value.length), label: newItem.value });
  // Limpiar la entrada
  newItem.value = '';
};

const activateEdition = (activate) => {
  editing.value = activate;
};
</script>

<template>
  <div class="header"></div>
  <h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
  </h1>

  <button v-if="editing" class="btn" @click="activateEdition(false)">
    Cancelar
  </button>
  <button v-else class="btn btn-primary" @click="activateEdition(true)">
    Agregar Articulo
  </button>

  <div class="add-item form">
    <a v-bind:href=" 'https://' + newItem" target="_blank">{{ newItem == "" ? "🔗 Link" : newItem}}</a>
    {{ 'https://' + newItem }} 
    <form v-on:submit.prevent="saveItem" v-if="editing">
      <!-- Entrada de texto -->
      <input
        type="text"
        placeholder="Add Item"
        v-model.trim="newItem"
      />
      <!-- Caja de selección de prioridad -->
      <label>
        <input type="checkbox" v-model="newItemHighPriority" />
        High Priority
      </label>
      <!-- Botón -->
      <button class="btn btn-primary">
        Save Item
      </button>
    </form>
  </div>

  <!-- Lista -->
  <ul>
    <li v-for="item in items" :key="item.id"> 🛍️ {{ item.label }} </li>
  </ul>
  <p v-if="items.length === 0">🥀 NO HAY ELEMENTOS EN LA LISTA 🥀</p>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>
