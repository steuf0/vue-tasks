<script setup>
import { reactive } from 'vue';

const emit = defineEmits(['create-todo']);
const todoState = reactive({
  todo: '',
  invalid: null,
  errMsg: '',
});

const createTodo = () => {
  emit('create-todo', todoState.todo);
};
</script>

<template>
  <div class="input-wrapper d-flex">
    <input type="text" v-model="todoState.todo" />
    <button class="btn btn-light" @click="createTodo">Criar</button>
  </div>
  <p>{{ todo }}</p>
</template>

<style lang="scss" scoped>
.input-wrapper {
  display: flex;
  transition: 250ms ease;
  border: 2px solid #41b080;
  border-radius: 0.25rem;
  &:focus-within {
    box-shadow: 0 -4px 6px -1px rgb(0 0 0 / 0.1),
      0 -2px 4px -2px rgb(0 0 0 / 0.1);
  }
  input {
    width: 100%;
    padding: 8px 6px;
    border: none;
    &:focus {
      outline: none;
    }
  }
  button {
    padding: 8px 16px;
    border: none;
  }
}
</style>
