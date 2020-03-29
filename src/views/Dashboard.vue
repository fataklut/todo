<template>
  <div class="dashboard">
    <v-container>
      <v-row> 
        <v-col>
          <h1>Todolist</h1>
        </v-col>
        <v-col>
          <Addtodo v-on:add-todo="addTodo" />
        </v-col>
      </v-row>
    </v-container>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" v-on:complete-todo="completeTodo" />
  </div>
</template>

<script>
import Todos from '../components/Todos'
import Addtodo from '../components/Addtodo'
import axios from 'axios'

export default {
  components: {
    Todos,
    Addtodo
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'todo 1',
          completed: false
        },
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo]
    },
    completeTodo(id) {
      let findIndex = this.todos.findIndex(e => e.id == id)
      this.todos[findIndex].completed = true
    }
  },
  created() {
    axios.get('https://jsonplaceholder.typicode.com/todos?_limit=7')
      .then(res => this.todos = res.data)
      .then(json => console.log(json))
      .catch(err => console.log(err))
  }
}
</script>
