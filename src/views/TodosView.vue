<script setup>
import TodoCreator from '../components/TodoCreator.vue';
import { uid } from 'uid';
import { ref } from 'vue';

const todoList = ref([]);

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: null,
    isEditing: null,
  });
};
</script>

<template>
  <main class="d-flex flex-column w-100">
    <h1 class="align-self-center mb-3">Criar tarefa</h1>
    <TodoCreator @create-todo="createTodo"></TodoCreator>
  </main>
</template>

<style lang="scss" scoped>
main {
  max-width: 500px;
  margin: 0 auto;
  padding: 40px 16px;
}
</style>
