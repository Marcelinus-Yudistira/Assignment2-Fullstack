<!-- TodoBoard.vue -->
<template>
    <div class="card">
    <h5 class="card-header">
      My Todo's
    </h5>
    <div class="card-body">
      <div class="todo-board">
      <TodoForm @addTodo="addTodo" />
      <TodoItems :todos="todos" 
                 @deleteTodo="deleteTodo" 
                 @changeStatusTodo="changeStatusTodo" />
      </div>
    </div>
  </div>
  </template>
  
  <script>
  import TodoForm from './TodoFormComponent.vue';
  import TodoItems from './TodoItemComponent.vue';
  
  export default {
    name: 'TodoBoard',
    components: {
      TodoForm,
      TodoItems
    },
    props: {
      todos: Array,
      addTodo: Function,
      deleteTodo: Function,
      changeStatusTodo: Function
    }
  };
  </script>

  <style>
    .card{
      padding: 0;
      width: 800px;
    }
  </style>
  