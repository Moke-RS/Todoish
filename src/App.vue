<template>
  <div id="app">
    <app-header app-name="Todoish" />
    <to-do-app />
  </div>
</template>

<script>
import AppHeader from './components/Header.vue';
import ToDoApp from './components/ToDoApp.vue';

export default {
  name: 'app',
  components: { AppHeader, ToDoApp }
}
</script>

<style>

body {
  margin: 0px;
  box-sizing: border-box;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

h1, h2 {
  font-weight: normal;
}
</style>
