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
  @include boxShadow;
  border-radius: $borderRadius;
  align-items: center;
  margin-bottom: 20px;

  h1 {
    color: $fontColor;
    margin: 10px;
  }

  #nav {
    a {
      font-weight: bold;
      text-decoration: none;
      color: $fontColor;
    }

    span {
      margin: 0px 10px 0px 10px;
    }

    a.router-link-exact-active {
      color: #1c976b;
    }
  }
}
</style>