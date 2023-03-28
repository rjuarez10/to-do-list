<template>
    <div>
      <h2>Tareas pendientes</h2>
      <ul>
        <li v-for="(task, index) in tasks" :key="index">
          <input type="checkbox" v-model="task.completed" />
          <span :class="{ completed: task.completed }">{{ task.description }}</span>
          <button @click="deleteTask(index)">Eliminar</button>
        </li>
      </ul>
      <form @submit.prevent="addTask">
        <input type="text" v-model="newTask" placeholder="Nueva tarea" />
        <button>Agregar tarea</button>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        tasks: [
          { description: 'Comprar leche', completed: false },
          { description: 'Hacer la tarea', completed: true },
          { description: 'Ir al gimnasio', completed: false },
        ],
        newTask: '',
      };
    },
    methods: {
      addTask() {
        if (this.newTask.trim() !== '') {
          this.tasks.push({
            description: this.newTask,
            completed: false,
          });
          this.newTask = '';
        }
      },
      deleteTask(index) {
        this.tasks.splice(index, 1);
      },
    },
  };
  </script>
  
  <style>
  .completed {
    text-decoration: line-through;
  }
  </style>
  