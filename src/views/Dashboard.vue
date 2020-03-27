<template>
  <div class="dashboard">
    <h1 class="mx-auto">Todolist</h1>
    <Todos v-bind:todos="todos" v-on:del-todo="deleteTodo" />
  </div>
</template>

<script>
import Todos from '../components/Todos'

export default {
  components: {
    Todos,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: 'Todo 1', 
          completed: true
        },
        {
          id: 2,
          title: 'Todo 2', 
          completed: false
        },
        {
          id: 3,
          title: 'Todo 3', 
          completed: true
        },
        {
          id: 4,
          title: 'Todo 4', 
          completed: false
        },
        {
          id: 5,
          title: 'Todo 5', 
          completed: false
        },
        {
          id: 6,
          title: 'Todo 6', 
          completed: false
        },
      ]
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id)
    }
  }
}
</script>
