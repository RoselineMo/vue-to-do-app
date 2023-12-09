<template>
  <div>
    <li>
      <span v-if="!todo.editing">{{ todo.text }}</span>
      <input v-else v-model="todo.text" @keyup.enter="editTodo" />
      <div className="btn">
        <button @click="deleteTodo">Delete</button>
        <button @click="editTodo">{{ todo.editing ? 'Save' : 'Edit' }}</button>
      </div>
    </li>
  </div>
</template>

<script>
export default {
  props: {
    todo: Object,
    index: Number,
  },
  methods: {
    deleteTodo() {
      this.$emit('deleteTodo', this.index);
    },
    editTodo() {
      this.$emit('editTodo', this.index);
    },
  },
};
</script>

<style scoped>
li {
  list-style-type: none;
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 0.8rem;
  align-items: center;
  justify-content: center;
  text-align: left; 
  margin-bottom: 20px;
}

ul {
  padding: 0;
}

li input {
  background: none;
  margin: 0;
}

button {
  border-radius: 5px;
  padding: 6px 12px;
  color: #fff;
  background-color: #e67e22;
  border: 2px solid transparent;
  font-weight: 600;
}

.btn {
  display: flex;
  align-items: center;
  justify-content: end;
  gap: 0.8rem;
}
</style>
