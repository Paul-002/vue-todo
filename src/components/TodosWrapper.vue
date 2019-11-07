<template>
  <div id="todos-wrapper">
    <div class="todo-item-container" v-bind:key="todo.id" v-for="todo in todos">
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

<style lang="scss">
@import "../Styles/_mixins.scss";
@import "../Styles/_variables.scss";

#todos-wrapper {
  margin-bottom: 20px;

  .todo-item-container {
    @include boxShadow;
    border-radius: $borderRadius;
    margin: 10px;
  }
}
</style>