<template>
  <div id="app">
  <div class="container mb-5">
    <img src="./assets/igloo-energy.png" width="50%">
  </div>
      <h1>To Do List</h1>
      <ToDoList></ToDoList>
  </div>
</template>

<script>
import ToDoList from "./components/ToDoList"


export default {
  name: 'app',
  components: {
    ToDoList
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px; 
}

h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
