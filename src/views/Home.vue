<template>
  <div id="app">
    <AddTodo @add-todo="addTodo"/>
    <Todos :todos="todos" @del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from "@/components/Todos.vue";
import AddTodo from "@/components/AddTodo.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Todos,
    AddTodo,
  },
  data() {
    return {
      todos: []
    };
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(response => this.todos = response.data)// eslint-disable-next-line
      .catch(err => console.log(err));
  },

  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        // eslint-disable-next-line no-unused-vars
        .then(response => this.todos = this.todos.filter(todo => todo.id !== id))// eslint-disable-next-line
        .catch(err => console.log(err));

      //this.todos = this.todos.filter(todo => todo.id !== id);
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo;

      axios
        .post("https://jsonplaceholder.typicode.com/todos", {
          title,
          completed
        })
        .then(response => this.todos = [...this.todos, response.data])// eslint-disable-next-line
        .catch(err => console.log(err));
    }
  }
};

</script>

<style scoped>
* {
  box-sizing: border-box;
  margin: 0px;
  padding: 0px;
}
body {
  line-height: 1.4;
  font-family: Arial, Helvetica, sans-serif;
}
.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}
</style>

