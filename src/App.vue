<!-- __previewjs__/Wrapper.vue -->

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import TaskManager from './components/TaskManager.vue'
import Counter from './components/Counter.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <Counter />
    </div>
  </header>

  <RouterView />
</template>

<style scoped></style>
