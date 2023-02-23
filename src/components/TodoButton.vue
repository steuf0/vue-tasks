<script setup>
const props = defineProps({
  btnText: String,
});
</script>

<template>
  <button
    class="btn btn-outline-primary"
    type="button"
    id="button-todo"
    @click="createTodo"
  >
    {{ btnText || 'OK' }}
  </button>
</template>

<style lang="scss" scoped></style>
