<template>
  <div id="app">
    <Todos v-bind:todos="todos" />
  </div>
</template>

<script>
import Todos from './components/Todos'
export default {
  name: 'app',
  components: {
    Todos,
  },
  data: ()=>({
    todos: [
      {
        id: 1,
        title: 'todo one',
        completed: false
      },
      {
        id: 2,
        title: 'todo two',
        completed: false
      },
      {
        id: 3,
        title: 'todo three',
        completed: false
      }
      ]
  })
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
</style>
