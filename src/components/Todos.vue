<template>
  <div>
    <h1>Todos</h1>
    <div v-for="(todo, id) in todos" :key="id">
      <TodoItem :todo="todo" @del-todo="$emit('del-todo', todo.id)" />
    </div>
  </div>
</template>
 
<script>
import TodoItem from "./TodoItem";
export default {
  name: "Todos",
  components: {
    TodoItem,
  },
  props: {
    todos: Array,
  },
};
</script>

<style scoped></style>