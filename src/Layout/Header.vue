<template>
  <header class="header">
    <div id="nav">
      <router-link to="/">Home</router-link>|
      <router-link to="/about">About</router-link>
    </div>
  </header>
</template>

<script>
export default {
  name: "Header"
};
</script>

<style scoped>
.header {
  width: 100%;
  height: 50px;
  background-color: bisque;
  border: 1px solid black;
}

#nav {
  height: 100%;
  padding: 30px;
  text-align: center;
  vertical-align: center;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>