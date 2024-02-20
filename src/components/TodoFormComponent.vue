<!-- TodoForm.vue -->
<template>
    <form @submit.prevent="handleAddTodo" class="mb-3">
      <div class="row">
        <div class="input-group">
          <div class="col-8"><input type="text" v-model="todoText" class="form-control" placeholder="Add new todo" required /></div>
          <div class="col-3"><input type="date" v-model="todoDate" class="form-control" required /></div>
          <div class="col-1"><button type="submit" class="btn btn-primary">Add</button></div>
        </div>
      </div>
    </form>
  </template>
  
  <script>
  export default {
    name: 'TodoForm',
    data() {
      return {
        todoText: '',
        todoDate: ''
      };
    },
    methods: {
      handleAddTodo() {
        if (this.todoText.trim() !== '' && this.todoDate !== '') {
          const date = new Date(this.todoDate);
          const options = { weekday: 'short', month: 'long', day: '2-digit', year: 'numeric' };
          const formattedDate = date.toLocaleDateString('en-US', options);
          
          const now = new Date();
          const dateNow = now.toLocaleDateString('en-US', options);

          this.$emit('addTodo', 
            this.todoText.trim(),
            formattedDate,
            dateNow
          );
          // this.$emit('addTodo', {
          //   text: this.todoText.trim(),
          //   date: this.todoDate
          // });
          this.todoText = '';
          this.todoDate = '';
          this.dateNow = '';
        }
      }
    }
  };
  </script>
  