<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <List></List>
  </div>
</template>

<script>
import List from './components/List.vue'

export default {
  name: 'App',
  components: {
    List
  }
}
</script>

<style>
* {
  padding:0;
  margin: 0;
  box-sizing: border-box;
}
li {
  list-style: none;
}
#app {
  position:relative;
  height: 100vh;
  width: 100vw;
}
</style>
