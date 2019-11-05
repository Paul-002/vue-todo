<template>
  <div>
    <div id="todos-wrapper" v-bind:key="todo.id" v-for="todo in todos">
      <SingleTodo v-on:del-todo="$emit('del-todo', todo.id)" v-bind:todo="todo" />
    </div>
  </div>
</template>

<script>
import SingleTodo from "./SingleTodo";
export default {
  name: "TodoWrapper",
  components: { SingleTodo },
  props: ["todos"]
};
</script>

<style scoped>
#todos-wrapper {
  border: 1px solid rgb(27, 201, 85);
  margin: 10px;
}
</style>