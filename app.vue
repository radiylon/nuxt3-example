<template>
  <div>
    {{ todos }}
    <button @click="createTodo()">Add Todo</button>
    <button @click="updateTodo({ })">Update Todo</button>
    <NuxtRouteAnnouncer />
    <NuxtWelcome />
  </div>
</template>

<script setup lang="ts">
  type Todo = {
    id: string;
    title: string;
    body: string;
    createdAt: Date;
    modifiedAt: Date;
  }

  type Todos = Todo[];
  
  const todos = ref<Todos>([]);
  const updateId = ref<Todo['title']>('');
  const updateTitle = ref('');
  const updateBody = ref('');

  function createTodo() {
    const newTodo = {
      id: `${todos.value.length + 1}`,
      title: `Todo ${todos.value.length + 1}`,
      body: '',
      createdAt: new Date(),
      modifiedAt: new Date()
    }
    todos.value.push(newTodo);
  }
</script>
