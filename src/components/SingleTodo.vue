<template>
  <div class="todo-item">
    <label class="container" v-bind:class="{'completed':todo.completed}">
      {{todo.title}}
      <input
        type="checkbox"
        class
        v-bind:checked="todo.completed"
        v-on:change="checkboxClick"
      />
      <span class="checkmark"></span>
    </label>
    <div @click="$emit('del-todo', todo.id)" class="del-button">X</div>
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

<style lang="scss">
@import "../Styles/_variables.scss";

.todo-item {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
  align-items: center;
  padding: 15px;

  .completed {
    text-decoration: line-through;
  }

  .del-button {
    color: #252525 !important;
    border-radius: $borderRadius;
    text-transform: uppercase;
    cursor: pointer;
    padding: 5px 8px 5px 8px;
    border: 2px solid #252525 !important;
    transition: all 0.2s ease 0s;

    &:hover {
      color: #f8fafb !important;
      background: #fec188;
      border-color: #f6b93b !important;
      transition: all 0.2s ease 0s;
    }
  }

  .container {
    display: flex;
    align-items: center;
    display: block;
    position: relative;
    padding-left: 35px;
    font-size: 20px;
    padding-top: 2px;
    margin-right: 20px;
    cursor: pointer;
    user-select: none;

    input {
      position: absolute;
      cursor: pointer;
      opacity: 0;
      height: 0;
      width: 0;

      &:hover input ~ .checkmark {
        background-color: #ccc;
      }

      &:checked ~ .checkmark {
        background-color: $checkboxColor;
      }
      &:checked ~ .checkmark:after {
        display: block;
      }
    }

    .checkmark {
      position: absolute;
      top: 0;
      left: 0;
      height: 25px;
      width: 25px;
      border-radius: 5px;
      background-color: #f8fafb;

      &:after {
        content: "";
        position: absolute;
        display: none;
        left: 9px;
        top: 5px;
        width: 5px;
        height: 10px;
        border: solid #f8fafb;
        border-width: 0 3px 3px 0;
        transform: rotate(45deg);
      }
    }
  }
}
</style>