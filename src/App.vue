<template>
  <div id="app">
    <div id="nav" class="has-text-centered">
      <router-link to="/">Game</router-link> |
      <router-link to="/why-i-made-this">Why + Process</router-link> |
      <router-link to="/pitch">Pitch</router-link> 
      <!-- |
      <router-link to="/about">About</router-link> -->
    </div>
    <router-view/>
    <Footer></Footer>
  </div>
</template>

<script>
import Footer from '@/components/Footer.vue';
    export default {
         components: {
           Footer
        }
    }
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
