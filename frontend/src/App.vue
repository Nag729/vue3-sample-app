<template>
  <div id="nav">
    <router-link to="/">Home</router-link> |
    <router-link to="/trends">Trends</router-link>
  </div>
  <router-view />
</template>

<style lang="scss">
// Noto Sans JP
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@300;400&display=swap');

#app {
  font-family: 'Noto Sans JP', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}

#nav {
  padding: 30px 0 15px 0;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
