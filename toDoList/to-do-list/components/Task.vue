<template>
    <li>
      <input type="checkbox" v-model="completed" />
      <span :class="{ completed: completed }">{{ description }}</span>
      <button @click="$emit('delete')">Eliminar</button>
    </li>
  </template>
  
  <script>
  export default {
    props: {
      description: String,
      completed: Boolean,
    },
  };
  </script>
  
  <style>
  .completed {
    text-decoration: line-through;
  }
  </style>
  