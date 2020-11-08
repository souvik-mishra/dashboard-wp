<template>
  <div id="app">
    <header class="app-header">
      <img class="app-header__img" alt="Vue logo" src="./assets/logo.png">
      <span class="app-header__title">My Dashboard</span>
    </header>    
    <task-list msg="Here are your tasks"/>
  </div>
</template>

<script>
import TaskList from './components/TaskList.vue'

export default {
  name: 'App',
  components: {
    TaskList
  }
}
</script>

<style>
body{
  height: 97.5vh;
}
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.app-header {
  text-align: start;
  background: #e8fae6;
  padding: 12px;  
  color: rgb(29, 95, 29);
}
.app-header__title {
  font-size: 3.2rem;
}
.app-header__img {
  height: 40px;
}
</style>
