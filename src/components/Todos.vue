<template>
  <div>
    <v-layout row wrap align-content-space-around>
        <v-flex class="mt-6" v-for="todo in todos" :key="todo.id">
            <v-card max-width="300px" :class="`mx-4 todo ${todo.completed}`">
                <v-card-title>{{ todo.title }}</v-card-title>
                <v-card-subtitle v-if="todo.completed">Task completed</v-card-subtitle>
                <v-card-subtitle v-else>Task incomplete</v-card-subtitle>
                <v-divider class="mx-4"></v-divider>
                <v-card-actions>
                    <v-btn text class="mx-auto" @click="$emit('complete-todo', todo.id)">Finished</v-btn>
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

<style>

.todo.true {
    border-left: 4px solid greenyellow;
}
.todo.false {
    border-left: 4px solid tomato;
}

</style>