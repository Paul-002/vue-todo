<template>
  <div id="app">
    <Header />
    <keep-alive include="home">
      <router-view />
    </keep-alive>
  </div>
</template>

<script>
import Header from "./Layout/Header";

export default {
  name: "app",
  components: {
    Header
  }
};
</script>

<style lang="scss">
@import "./Styles/_mixins.scss";
@import "./Styles/_variables.scss";

* {
  box-sizing: border-box;
  padding: 0px;
  margin: 0px;
}

body {
  @include flexCenter(row, center);
  background-color: #f8fafb;
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  color: $fontColor;

  #app {
    min-width: 40%;
    padding: 10px;
  }
}
</style>
