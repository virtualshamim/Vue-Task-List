<template>
  <div id="app">
    <h1>Task Manager</h1>
    <TaskList :tasks="tasks" />
  </div>
</template>

<script setup>
import { ref } from 'vue';
import TaskList from './components/TaskList.vue';

const tasks = ref([
  { name: 'Task 1', time: 30 },
  { name: 'Task 2', time: 40 },
  { name: 'Task 3', time: 60 },
  { name: 'Task 4', time: 45 },
  { name: 'Task 5', time: 50 },
]);
</script>
