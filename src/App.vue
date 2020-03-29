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

export default {
  name: 'App',
  components: {
    Navbar,
  }
};
</script>


