<!-- __previewjs__/Wrapper.vue -->

<script setup>
import { ref, computed } from 'vue'

const tasks = ref([])
const filter = ref('all')
const message = ref('')

// add new task to array
const addTask = (value) => {
  if (message.value == '') {
    return
  }
  tasks.value.push({ name: value, status: true })
  message.value = ''
}

// computed task list based on filter
const filteredTasks = computed(() => {
  if (filter.value === 'active') {
    return tasks.value.filter((task) => task.status)
  } else if (filter.value === 'done') {
    return tasks.value.filter((task) => !task.status)
  } else {
    return tasks.value
  }
})
</script>

<template>
  <h1>Gestionnaire des Taches</h1>
  <input v-model="message" placeholder="Ajoutez une nouvelle tache" />
  <button @click="addTask(message)">Ajouter</button>
  <h2>Toutes les taches:</h2>
  <ul>
    <li
      v-for="task in filteredTasks"
      :key="task.name"
      :class="{ doneTask: !task.status }"
      @click="task.status = !task.status"
    >
      {{ task.name }}
    </li>
  </ul>
  <div class="buttons">
    <button @click="filter = 'all'">All</button>
    <button @click="filter = 'active'">Active</button>
    <button @click="filter = 'done'">Done</button>
  </div>
</template>

<style scoped>
.buttons {
  top: 700px;
  position: absolute;
}
button {
  margin-inline: 5px;
  height: 40px;
  width: 80px;
}
input {
  width: 250px;
  height: 40px;
  margin-block: 20px;
}
.doneTask {
  text-decoration: line-through;
}
li {
  font-size: 20px;
  border: 1px solid transparent;
  border-radius: 4px;
}
</style>
