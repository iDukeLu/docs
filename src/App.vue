<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<script>
  export default {
    name: 'App'
  }
</script>

<style>
  /*VUE中须将挂载的#app样式也设为100%*/
  html, body, #app {
    height: 100%;
    width: 100%;
  }
  .main {
    height: 100%;
    width: 100%;
  }
</style>
