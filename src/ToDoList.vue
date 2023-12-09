<template>
  <div>
    <ul>
      <TodoItem
        v-for="(todo, index) in todos"
        :key="index"
        :todo="todo"
        :index="index"
        @deleteTodo="deleteTodo"
        @editTodo="editTodo"
      />
    </ul>
  </div>
</template>

<script>
import TodoItem from './ToDoItem.vue';

export default {
  props: {
    todos: Array,
  },
  methods: {
    deleteTodo(index) {
      this.$emit('deleteTodo', index);
    },
    editTodo(index) {
      this.$emit('editTodo', index);
    },
  },
  components: {
    TodoItem,
  },
};
</script>
