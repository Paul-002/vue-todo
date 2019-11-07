<template>
  <div id="form-wrapper">
    <form @submit="addTodo">
      <input
        class="input-text"
        autocomplete="off"
        v-model="title"
        type="text"
        name="title"
        placeholder="Add new Todo..."
      />
      <input type="submit" value="ADD" />
    </form>
  </div>
</template>

<script>
export default {
  name: "AddTodo",
  data() {
    return {
      title: ""
    };
  },
  methods: {
    addTodo(e) {
      e.preventDefault();
      if (this.title.trim()) {
        const newTodo = {
          title: this.title,
          completed: false
        };
        this.$emit("add-todo", newTodo);
        this.title = "";
      }
    }
  }
};
</script>

<style lang="scss">
@import "../Styles/_variables.scss";
@import "../Styles/_mixins.scss";

#form-wrapper {
  @include flexCenter(column, flex-start);
  margin-bottom: 20px;
  height: 70px;

  input[type="text"] {
    @include boxShadow;
    @include basicInputStyle;

    &:focus {
      outline: none;
      border-color: $color6;
      transform: translateY(-2px);
    }

    &::placeholder {
      font-size: 14px;
      color: $color7;
    }
  }

  input[type="submit"] {
    @include boxShadow;
    @include basicInputStyle;
    width: 60px;
    cursor: pointer;
    font-weight: bold;

    &:hover {
      color: $color4;
      background-color: $color2;
      transform: translateY(-2px);
    }

    &:focus {
      outline: none;
    }
  }
}
</style>