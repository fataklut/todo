<template>
  <div>
    <v-container>
        <v-row style="justify-content: center">
            <v-col v-for="todo in todos" :key="todo.id" cols="auto">
                <v-card :class="`mx-4 todo ${todo.completed}`">
                <v-card-title>{{ todo.title }}</v-card-title>
                <v-divider class="mx-4"></v-divider>
                <v-card-actions>
                    <v-btn text class="mx-2 success darken-1" @click="$emit('complete-todo', todo.id)">Finished</v-btn>
                    <v-btn text class="red white--text mx-2" @click="$emit('del-todo', todo.id)">Remove</v-btn>
                </v-card-actions>
            </v-card>
            </v-col>
        </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
    name: 'Todos',
    props: ['todos']
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