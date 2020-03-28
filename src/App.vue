<template>
  <v-app>
    <link href="https://fonts.googleapis.com/css?family=Material+Icons" rel="stylesheet">
    <Navbar />
    <v-content class="mt-6 mx-12">
      <router-view></router-view>
    </v-content>
  </v-app>
</template>

<script>
import Navbar from './components/Navbar'
import DashboardVue from './views/Dashboard.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Navbar,
  },
  methods: {
    created() {
      axios.get('https://jsonplaceholder.typicode.com/todos?_limit=8')
        .then(res => DashboardVue.todos = res.data)
        .catch(err => console.log(err))
      alert()
    },
  }
};
</script>

