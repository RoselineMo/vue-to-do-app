<template>
  <div id="app">
    <div className="container">
      <h1>My Vue Todo App</h1>
      <input
        v-model="newTodo"
        @keyup.enter="addTodo"
        placeholder="Add a new item"
        maxLength="30"
      />
      <TodoList :todos="todos" @deleteTodo="deleteTodo" @editTodo="editTodo" />
    </div>
  </div>
</template>

<script>
import TodoList from './ToDoList.vue';

export default {
  data() {
    return {
      newTodo: '',
      todos: [],
    };
  },
  methods: {
    addTodo() {
      if (this.newTodo.trim() !== '') {
        this.todos.push({ text: this.newTodo, editing: false });
        this.newTodo = '';
      }
    },
    deleteTodo(index) {
      this.todos.splice(index, 1);
    },
    editTodo(index) {
      this.todos[index].editing = !this.todos[index].editing;
    },
  },
  components: {
    TodoList,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  text-align: center;
  background-color: #fdf2e9;
  border: 0.5px solid #ccc;
  border-radius: 10px;
  height: 100vh;
}

h1 {
  padding-top: 20px;
  color: #45260a;
}

input {
  padding: 10px;
  margin-bottom: 20px;
  max-width: 25rem;
  font-size: 16px;
  border-radius: 10px;
  border: 2px solid #ccc;
}

.container {
  max-width: 150rem;
  margin: 0 auto;
  padding: 0.5rem 3.2rem;
}
</style>
