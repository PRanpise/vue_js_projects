<template>
  <div id="app">
    <input v-model="newTodoItem" v-on:keyup.enter="addTodos" />
    <button @click="addTodos"> 
        + ADD
    </button>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo"/>
  </div>
</template>

<script>
import Todos from './components/Todos'
export default {
  name: 'App',
  components: {
    Todos
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Todo A',
          completed: false,
        },
        {
          id: 2,
          title: 'Todo B',
          completed: true,
        }
      ],
      count: 2,
      newTodoItem: ''
    }
  },
  methods: {
    addTodos() {
      this.count += 1;
      this.todos.push({ id: this.count, title: this.newTodoItem, completed: false })
      this.newTodoItem = ''
    },
    deleteTodo(id) {
      //here we are using high order array method "filter"
      this.todos = this.todos.filter( todo => todo.id !== id);
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
