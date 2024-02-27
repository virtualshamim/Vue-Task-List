<template>
    <div>
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          {{ task.name }} - {{ task.time }}
          <button @click="editTask(index)">Edit</button>
        </li>
      </ul>
      <TaskEditForm v-if="showEditForm" :task="selectedTask" @submit="updateTask" />
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  import TaskEditForm from './TaskEditForm.vue';
  
  const tasks = ref([
    { name: 'Task 1', time: 30 },
    { name: 'Task 2', time: 40 },
    { name: 'Task 3', time: 60 },
    { name: 'Task 4', time: 45 },
    { name: 'Task 5', time: 50 },
  ]);
  
  const showEditForm = ref(false);
  const selectedTask = ref(null);
  
  const editTask = (index) => {
    selectedTask.value = { ...tasks.value[index] };
    showEditForm.value = true;
  };
  
  const updateTask = (updatedTask) => {
    const index = tasks.value.findIndex(task => task.name === updatedTask.name);
    if (index !== -1) {
      tasks.value[index] = updatedTask;
      showEditForm.value = false;
    }
  };
  </script>
  