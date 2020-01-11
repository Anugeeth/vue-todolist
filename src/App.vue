<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Header from './components/layout/Header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'

export default {
  name: 'app',
  components: {
    Header,
    Todos,
    AddTodo
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
        completed: true
      },
      {
        id: 3,
        title: 'todo three',
        completed: false
      }
      ]
  }),
  methods: {
    deleteTodo(id){
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(newTodo){
      this.todos = [...this.todos, newTodo]
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
 body {
   font-family: Arial, Helvetica, sans-serif;
   line-height: 1.4;
 }
 .btn{
   display: inline-block;
   border: none;
   background: #555;
   color: #fff;
   cursor: pointer;
 }
 .btn::hover {
   background: #666;
 }
</style>
