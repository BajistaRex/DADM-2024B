<script setup>
  import { ref } from 'vue';
  // Modelo
  const header = ref('App lista de compras');
  // ----Items----
  // Item-Model
  const items = ref([ 
    {id: '0', label: '10 Bolillos'},
    {id: '1', label: '1 Lata Frijoles'},
    {id: '2', label: '1 Chelas'},
    {id: '3', label: '1 Nutella'},
  ]);
  // Item-Method
const saveItem = () => {
  // Add new Item
  items.value.push({id: items.value.length + 1, label: newItem.value});
  // Clean the input
  newItem.value = '';
};

  const newItem = ref('');
  const newItemHighPriority = ref(false);

</script>

<template>
  <h1> <i class="material-icons shopping-cart-icon">local_mall</i> {{ header }}
    
  </h1>
  <div class="add-item form">
<!-- Agrupando en un div las entradas -->
<form v-on:submit.prevent="saveItem">
<!-- entrada de texto -->
	<input
    type="text"
    placeholder="Add Item"
    v-model.trim="newItem"
  />
    <!-- Caja de seleccion de prioridad -->
    <label>
      <input type="checkbox" v-model="newItemHighPriority" />
      High Priority
    </label>
    <!-- Boton -->
    <button
      class="btn btn-primary"
    >
      Save Item
    </button>
  </form>
</div>

<!-- Lista -->
<ul>
    <li v-for="item in items" :key="item.id"> 🛍️ {{ item.label }} </li>
  </ul>
</template>

<style scoped>
.shopping-cart-icon {
  font-size: 2rem;
}
</style>
