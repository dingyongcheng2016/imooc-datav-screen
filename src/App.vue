<template>
  <div id="app">
    <screen />
  </div>
</template>

<script>
 import Screen from './views/Screen'

 export default {
   components: {
     Screen
   }
 }
</script>

<style lang="scss">
  html, body {
    margin: 0;
    padding: 0;
    width: 100%;
    height: 100%;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
  }
</style>
