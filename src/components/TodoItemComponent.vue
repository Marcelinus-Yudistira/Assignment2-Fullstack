<!-- TodoItems.vue -->
<template>
  <div>
    <div v-for="todo in todos" :key="todo.id" class="row"  style="text-align: left">
      <div class="col-1 d-flex align-items-center">
        <div class="form-check">
          <input type="checkbox" :id="'todo-'+todo.id" v-model="todo.completed" @change="handleChangeStatus(todo.id)" class="form-check-input" :checked="todo.completed" />
        </div>
      </div>
      <div class="col-7 d-flex align-items-center"><label :for="'todo-'+todo.id" :class="{ 'completed': todo.completed }" class="form-check-label">{{ todo.text }}</label></div>
      <div class="col-3 d-flex align-items-center justify-content-end">
        <button type="button" class="btn btn-secondary btn-sm">{{ todo.date }}</button>
      </div>
      <div class="col-1 text-end" style="font-size: 10px;">
        <button @click="handleDelete(todo.id)" class="btn btn-danger">
          <i class="bi bi-trash"></i>
        </button>
        {{ todo.dateNow }}
      </div>
      <hr class="col-12 my-2">
    </div>
  </div>
</template>

  
  <script>
  export default {
    name: 'TodoItems',
    props: {
      todos: Array
    },
    methods: {
      handleDelete(todoId) {
        this.$emit('deleteTodo', todoId);
      },
      handleChangeStatus(todoId) {
        this.$emit('changeStatusTodo', todoId);
      }
    }
  };
  </script>
  
  <style scoped>
  .completed {
    text-decoration: line-through;
  }

  </style>
  