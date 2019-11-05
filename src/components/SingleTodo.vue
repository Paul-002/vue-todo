<template>
  <div class="todo-item" v-bind:class="{'completed':todo.completed}">
    <p>
      <input v-bind:checked="todo.completed" v-on:change="checkboxClick" type="checkbox" />
      {{todo.title}}
    </p>
    <button @click="$emit('del-todo', todo.id)" class="del-button">X</button>
  </div>
</template>

<script>
export default {
  name: "SingleTodo",
  props: ["todo"],
  methods: {
    checkboxClick() {
      this.todo.completed = !this.todo.completed;
    }
  }
};
</script>

<style scoped>
.todo-item {
  display: flex;
  flex-direction: row;
  position: relative;
  padding: 15px;
}

.completed {
  text-decoration: line-through;
}

.del-button {
  position: absolute;
  right: 10px;
  top: 0px;
  padding: 10px;
}
</style>