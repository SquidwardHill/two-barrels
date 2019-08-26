<template>
  <div id="app">
    <div id="nav" class="has-text-centered">
      <router-link to="/">Game</router-link> |
      <router-link to="/why-i-made-this">But Why</router-link> |
      <router-link to="/about">Me</router-link>
    </div>
    <router-view/>
  </div>
</template>

<script>

</script>
<style lang="scss">
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
}
#nav {
  padding: 30px;
  a {
    font-weight: bold;
    color: #2c3e50;
    &.router-link-exact-active {
      color: map-get($map: $colors, $key: primary )
    }
  }
}

</style>
