<script setup>
import TodoCreator from '../components/TodoCreator.vue';
import { uid } from 'uid';
import { ref } from 'vue';
import TodoItem from '../components/TodoItem.vue';
import { Icon } from '@iconify/vue';

//reactive value
const todoList = ref([]);

//gets list from Local Storage
const fetchFromLocalStorage = () => {
  const storedList = JSON.parse(localStorage.getItem('todoList'));

  if (storedList) {
    todoList.value = storedList;
  }
};

fetchFromLocalStorage();

//sets list to Local Storage
const setToLocalStorage = () => {
  localStorage.setItem('todoList', JSON.stringify(todoList.value));
};

const createTodo = (todo) => {
  todoList.value.push({
    id: uid(),
    todo,
    isCompleted: null,
    isEditing: null,
  });

  setToLocalStorage();
};

//toggle task completed
const toggleCompletion = (position) => {
  todoList.value[position].isCompleted = !todoList.value[position].isCompleted;
  setToLocalStorage();
};

//toggle edit value (input)
const toggleEdit = (position) => {
  todoList.value[position].isEditing = !todoList.value[position].isEditing;
  setToLocalStorage();
};

//change task title
const updateTodo = (newValue, position) => {
  todoList.value[position].todo = newValue;
  setToLocalStorage();
};

//delete task
const deleteTodo = (id) => {
  todoList.value = todoList.value.filter((task) => task.id !== id);
  setToLocalStorage();
};
</script>

<template>
  <main class="d-flex flex-column w-100">
    <h1 class="align-self-center mb-3">Criar tarefa</h1>
    <TodoCreator @create-todo="createTodo" />

    <ul class="todo-list" v-if="todoList.length > 0">
      <TodoItem
        v-for="(todo, index) in todoList"
        :todo="todo"
        :index="index"
        @toggle-complete="toggleCompletion"
        @edit-todo="toggleEdit"
        @update-todo="updateTodo"
        @delete-todo="deleteTodo"
      />
    </ul>
    <p class="no-tasks" v-else>
      <Icon icon="emojione:sad-but-relieved-face" width="22" />
      <span>Você não tem tarefas a fazer. Adicione uma!</span>
    </p>
  </main>
</template>

<style lang="scss" scoped>
main {
  max-width: 500px;
  margin: 0 auto;
  padding: 40px 16px;

  ul {
    padding: 0;
  }
  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top: 24px;
    gap: 20px;
  }
  .no-tasks {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
  }
}
</style>
