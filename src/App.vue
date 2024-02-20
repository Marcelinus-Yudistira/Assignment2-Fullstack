<!-- App.vue -->
<template>
  <div id="app">
    <TodoBoard :todos="todos" 
               :addTodo="addTodo" 
               :deleteTodo="deleteTodo" 
               :changeStatusTodo="changeStatusTodo" />
  </div>
</template>

<script>
import { reactive } from 'vue';
import TodoBoard from './components/TodoBoardComponent.vue';

export default {
  name: 'App',
  components: {
    TodoBoard
  },
  setup() {
    const todos = reactive([
      { id: 1, text: 'Learn HTML', date: 'Wed, Dec 12 2023', dateNow: 'Mon, Dec 05 2023', completed: false },
      { id: 2, text: 'Lerarning CSS', date: 'Tue, Dec 29 2023', dateNow: 'Thu, Dec 01 2023', completed: false }
    ]);

    const addTodo = (todoText, todoDate, dateNow) => {
      const newTodo = {
        id: todos.length + 1,
        text: todoText,
        date: todoDate,
        dateNow: dateNow,
        completed: false
      };
      todos.push(newTodo);
    };

    const deleteTodo = (todoId) => {
      const index = todos.findIndex(todo => todo.id === todoId);
      if (index !== -1) {
        todos.splice(index, 1);
      }
    };

    const changeStatusTodo = (todoId) => {
      const todo = todos.find(todo => todo.id === todoId);
    };

    return {
      todos,
      addTodo,
      deleteTodo,
      changeStatusTodo
    };
  }
};
</script>
