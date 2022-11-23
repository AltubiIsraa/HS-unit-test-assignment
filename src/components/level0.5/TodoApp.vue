<script setup>
import { ref } from 'vue';

const newTodo = ref('');
const todos = ref([
  {
    id: 1,
    text: 'Learn Vue.js 3',
    completed: false,
  },
]);
function addTodo() {
  todos.value.push({
    id: todos.value.length + 1,
    text: newTodo.value,
    completed: false,
  });
}
</script>
<template>
  <!-- <div data-test="todo">
    {{ todos[0].text }}
  </div> -->
  <div>
    <div
      v-for="todo in todos"
      :key="todo.id"
      data-test="todo"
      :class="{ completed: todo.completed }"
    >
      <input
        type="checkbox"
        v-model="todo.completed"
        data-test="todo-checkbox"
      />
      <span>{{ todo.text }}</span>
    </div>
  </div>

  <input type="text" data-test="new-todo-input" v-model="newTodo" />
  <button @click="addTodo" data-test="new-todo-btn">Add todo</button>
</template>
