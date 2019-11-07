<template>
  <header id="header">
    <h1>Vue todo app</h1>
    <div id="nav">
      <router-link to="/">Home</router-link>
      <span>|</span>
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style lang="scss">
@import "../Styles/_mixins.scss";
@import "../Styles/_variables.scss";

#header {
  @include flexCenter(row, space-around);
  border-bottom: 2px solid $color2;
  align-items: center;
  margin-bottom: 20px;

  h1 {
    color: $color2;
    margin: 10px;
  }

  #nav {
    margin-right: 10px;
    a {
      text-decoration: none;
      font-weight: bold;
      color: $color2;
    }

    span {
      margin: 0px 10px 0px 10px;
    }

    a.router-link-exact-active {
      color: $color1;
    }
  }
}
</style>