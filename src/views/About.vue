<template>
  <div id="about">
    <h2>Hello! 👋</h2>
    <p>
      This is my first contact with
      <b>Vue.js</b> library. I hope you enjoy!
      <br />
      <br />If you interested my other projects, check this
      <a
        target="n"
        rel="noopener"
        href="https://github.com/Paul-002/"
      >Github</a>
      page. 🔥
    </p>
  </div>
</template>

<style lang="scss">
@import "../Styles/_variables.scss";
@import "../Styles/_mixins.scss";

#about {
  @include boxShadow;
  border-radius: $borderRadius;

  h2 {
    padding: 10px;
  }

  p {
    padding: 10px 10px 20px 10px;
    font-size: 20px;
    text-align: justify;

    a {
      text-decoration: none;
    }
  }
}
</style>