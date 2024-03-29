<template>
  <div>
    <NavbarPage/>
    <router-view />
  </div>

</template>

<script>

import NavbarPage from './components/NavbarPage.vue'


export default {
  components: {
    NavbarPage
  }
}
</script>

<style>
body {
  background-color: antiquewhite;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  max-width: 600px;
  margin: 0 auto;
  color: #2c3e50;
}

</style>
