<template>
  <div id="container">
    <TodosWrapper v-bind:todos="todos" v-on:del-todo="deleteTodo" />
    <AddTodo @add-todo="addTodo" />
  </div>
</template>

<script>
import TodosWrapper from "../components/TodosWrapper";
import AddTodo from "../components/AddTodo";
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
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/todos?_limit=10")
      .then(res => (this.todos = res.data))
      .catch(err => alert(err));
  },

  methods: {
    deleteTodo(id) {
      axios
        .delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(() => (this.todos = this.todos.filter(todo => todo.id !== id)))
        .catch(err => alert(err));
    },

    addTodo(newTodo) {
      const { title, complete } = newTodo;
      axios
        .post("https://jsonplaceholder.typicode.com/todos", { title, complete })
        .then(res => (this.todos = [res.data, ...this.todos]))
        .catch(err => alert(err));
    }
  }
};
</script>

<style scoped>
#container {
  border: 1px solid blue;
}
</style>