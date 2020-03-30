<template>
  <div class="dashboard">
    <v-container>
      <v-row class="text-center"> 
        <v-col> 
          <h1>Todolist</h1>
        </v-col>
        <v-col>
          <Addtodo v-on:add-todo="addTodo" />
        </v-col>
      </v-row>
    </v-container>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" v-on:complete-todo="completeTodo" v-on:rename-todo="renameTodo" />
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
      todos: []
    }
  },
  methods: {
    deleteTodo(id) {
      axios.delete(`https://jsonplaceholder.typicode.com/todos/${id}`)
        .then(this.todos = this.todos.filter(todo => todo.id !== id))
        .catch(err => console.log(err))
    },
    addTodo(newTodo) {
      const { title, completed } = newTodo
      axios.post('https://jsonplaceholder.typicode.com/todos', 
      {
        title,
        completed
      }).then(res => this.todos = [...this.todos, res.data])
        .catch(err => console.log(err))
    },
    completeTodo(id) {
      let findIndex = this.todos.findIndex(e => e.id == id)
      this.todos[findIndex].completed = true
    },
    renameTodo(newIdAndName) {
      let findIndex = this.todos.findIndex(e => e.id == newIdAndName[0])
      this.todos[findIndex].title = newIdAndName[1]
      alert()
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
