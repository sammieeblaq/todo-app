<template>
  <div>
    <AddTodo @add-todo="addTodo" />
    <Todos :todos="todos" @del-todo="deleteTodo" />
  </div>
</template>


<script>
import Todos from "../components/Todos";
import AddTodo from "../components/AddTodo";
import axios from "axios";
export default {
  name: "Home",
  components: {
    AddTodo,
    Todos,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    // async deleteTodo(id) {
    //   let response = await axios.delete(
    //     `https://jsonplaceholder.typicode.com/posts${id}`
    //   );
    //   let result = await response.data;
    //   result = this.todos.filter((todo) => todo.id !== id);
    // },
    async addTodo(newTodo) {
      const { title, completed } = newTodo;
      const post = await axios.post(
        "https://jsonplaceholder.typicode.com/posts",
        {
          title,
          completed,
        }
      );
      const data = await post.data;
      this.todos.push(data);
    },
  },
  async created() {
    try {
      const response = await axios.get(
        "https://jsonplaceholder.typicode.com/users/1/todos?_limit=5"
      );
      const data = await response.data;
      this.todos = data;
    } catch (error) {
      console.error(error);
    }
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}
body {
  font-family: Arial, Helvetica, sans-serif;
  line-height: 1.4;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #ffffff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:hover {
  background: #666;
}
</style>
