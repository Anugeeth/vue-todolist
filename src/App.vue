
<template>
  <div id="app">
    <Header />
    <AddTodo v-on:add-todo="addTodo"/>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import axios from 'axios'
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
    todos: [],
  }),
  methods: {
    deleteTodo(id){
      axios.delete('https://jsonplaceholder.typicode.com/todos/${id}')
      // eslint-disable-next-line no-unused-vars
      .then(res => {
              this.todos = this.todos.filter(todo => todo.id !== id)
      })
      // eslint-disable-next-line no-console
      .catch(err => console.log(err))
    },
    addTodo(newTodo){
      const { title, completed} = newTodo;
      axios.post('https://jsonplaceholder.typicode.com/todos',{ 
        title,
        completed
      })
      .then(res => {
          this.todos = [...this.todos, res.data]
      })
      // eslint-disable-next-line no-console
      .catch(err => console.log(err))
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=5')
    .then(res => {
      this.todos = res.data
      })
    // eslint-disable-next-line no-console
    .catch(err => console.log(err))
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
