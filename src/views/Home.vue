<template>
  <div id="home-container">
    <TodosWrapper v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <AddTodo @add-todo="addTodo" />
  </div>
</template>

<script>
import TodosWrapper from "../components/TodosWrapper";
import AddTodo from "../components/AddTodo";
import uuid from "uuid";
import axios from "axios";

export default {
  name: "home",
  components: {
    TodosWrapper,
    AddTodo
  },
  data() {
    return {
      todos: []
    };
  },

  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => (this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => alert(err));
    },

    addTodo(newTodo) {
      axios
        .post("https://jsonplaceholder.typicode.com/todos", newTodo)
        .then(res => {
          res.data.id = uuid.v4();
          this.todos = [res.data, ...this.todos];
        })
        .catch(err => alert(err));
    }
  },

  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then(res => {
        this.todos = res.data;
      })
      .catch(err => alert(err));
  }
};
</script>