<template>
  <section class="section">
    <div class="container">
      <div id="nav">
        <router-link to="/">Home</router-link> |
        <router-link to="/list">List</router-link>
      </div>
      <router-view />
    </div>
  </section>
</template>

<style lang="scss">
// Noto Sans JP
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400&display=swap');

html {
  min-height: 100%;
  background: #1c92d2; /* fallback for old browsers */
  background: -webkit-linear-gradient(
    to top,
    #f2fcfe,
    #1c92d2
  ); /* Chrome 10-25, Safari 5.1-6 */
  background: linear-gradient(
    to top,
    #f2fcfe,
    #1c92d2
  ); /* W3C, IE 10+/ Edge, Firefox 16+, Chrome 26+, Opera 12+, Safari 7+ */

  // modify bulma section
  .section {
    padding: 2rem 1.5rem;
  }
}

#app {
  font-family: 'Noto Sans JP', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

#nav {
  text-align: center;
  padding: 3vh 0 2vh 0;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: azure;
    }
  }
}
</style>
