<template>
  <div id="nav">
    <router-link to="/console">Console</router-link> | 
    <router-link to="/breakpoint">Breakpoint</router-link> |
    <router-link to="/test">Test</router-link>
  </div>
  <router-view/>
</template>

<style lang="less">
html,body {
  height: 100%;
}
#app {
  height: 100%;
}
#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
