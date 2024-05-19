<script setup>
import { ref } from 'vue'
const value = ref(0)
</script>

<template>
  <h2>Compteur Dynamique</h2>
  <p>La valeur actuelle du compteur est: {{ value }}</p>
  <button @click="value++">Incrémenter</button>
  <button @click="value--">Décrémenter</button>
  <button @click="value = 0">Réinitialiser</button>
</template>

<style scoped>
h2 {
  color: rgb(11, 11, 146);
}
</style>
