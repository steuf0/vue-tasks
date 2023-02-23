<script setup>
import { reactive } from 'vue';
import TodoButton from './TodoButton.vue';

const emit = defineEmits(['create-todo']);
const todoState = reactive({
  todo: '',
  invalid: null,
  errMsg: '',
});

const createTodo = () => {
  todoState.invalid = null;

  if (todoState.todo !== '') {
    emit('create-todo', todoState.todo);
    todoState.todo = '';
    return;
  }

  todoState.invalid = true;
  todoState.errMsg = 'O título da tarefa não pode ser vazio.';
};
</script>

<template>
  <div class="input-group">
    <input
      type="text"
      class="form-control"
      placeholder="Insira o título da tarefa"
      aria-label="Insira o título da tarefa"
      aria-describedby="button-todo"
      :class="{ 'is-invalid': todoState.invalid }"
      v-model="todoState.todo"
    />
    <TodoButton @click="createTodo" btnText="Criar" />
  </div>
  <p class="err-msg text-danger mt-1" v-show="todoState.invalid">
    {{ todoState.errMsg }}
  </p>
</template>

<style lang="scss" scoped></style>
