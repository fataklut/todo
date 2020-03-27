<template>
  <div>
    <v-layout row wrap justify="center" align="center">
        <v-flex class="mt-6" v-bind:key="todo.id" v-for="todo in todos">
            <v-card max-width="250px" v-bind:class="{'green lighten-4':todo.completed}">
                <v-card-title>{{ todo.title }}</v-card-title>
                <v-card-subtitle v-if="todo.completed">Task completed</v-card-subtitle>
                <v-card-subtitle v-else>Task incomplete</v-card-subtitle>
                <v-card-text>Lorem ipsum dolor sit amet, 
                    consectetur adipisicing elit. Nobis, qui!</v-card-text>
                <v-card-actions>
                    <v-btn text class="mx-auto">Finished</v-btn>
                    <v-btn text class="red white--text mx-auto" @click="$emit('del-todo', todo.id)">Remove</v-btn>
                </v-card-actions>
            </v-card>
        </v-flex>
    </v-layout>
  </div>
</template>

<script>
export default {
    name: 'Todos',
    props: ['todos'],
}
</script>

<style scoped>

</style>