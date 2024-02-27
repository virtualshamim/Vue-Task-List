<template>
    <div>
      <h2>Edit Task</h2>
      <form @submit.prevent="submitForm">
        <div>
          <label for="name">Name:</label>
          <input id="name" type="text" v-model="editedTask.name">
        </div>
        <div>
          <label for="time">Time:</label>
          <input id="time" type="number" v-model.number="editedTask.time">
        </div>
        <button type="submit">Submit</button>
      </form>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const editedTask = ref({ ...props.task });
  
  const submitForm = () => {
    emit('submit', editedTask.value);
  };
  </script>
  
  <script>
  import { defineProps, defineEmit } from 'vue';
  
  const props = defineProps({
    task: {
      type: Object,
      required: true,
    },
  });
  
  const emit = defineEmit(['submit']);
  </script>
  