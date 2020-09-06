<template>
  <div class="todo__item" :class="{ is__completed: todo.completed }">
    <p>
      <input type="checkbox" @change="markComplete" />
      {{ todo.title }}
      <button @click="$emit('del-todo', todo.id)" class="del">x</button>
    </p>
  </div>
</template>

<script>
export default {
  name: "TodoItem",
  props: ["todo"],

  methods: {
    markComplete() {
      this.todo.completed = !this.todo.completed;
    },
  },
};
</script>

<style scoped>
.todo__item {
  background: #f4f4f4;
  padding: 10px;
  border-bottom: 1px solid #ccc;
}

.is__completed {
  text-decoration: line-through;
}

.del {
  background: #ff0000;
  color: #fff;
  border: none;
  padding: 5px 9px;
  border-radius: 50%;
  cursor: pointer;
  float: right;
}
</style>