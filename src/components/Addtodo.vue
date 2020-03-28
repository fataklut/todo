<template>
  <div>
    <v-dialog
      v-model="dialog"
      width="500"
    >
      <template v-slot:activator="{ on }">
        <v-btn
          class="success white--text"
          v-on="on"
        >
          Add new todo
        </v-btn>
      </template>

      <v-card>
        <v-card-title
          class="headline grey lighten-2"
          primary-title
        >
          Add new todo
        </v-card-title>

        <v-card-text>
          <v-form class="px-3 pt-3">
              <v-text-field title="Title" v-model="title" label="title" :rules="inputRules" class="mb-3"></v-text-field>
              <v-btn color="success" @click="addTodo">Add todo</v-btn>
          </v-form>
        </v-card-text>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        dialog: false,
        title: '',
        inputRules: [
            v => v.length >= 3 || 'Minimum length is 3 characters'
        ]
      }
    },
    methods: {
        addTodo() {
            const newTodo = {
                title: this.title,
                completed: false,
            }
            this.$emit('add-todo', newTodo)
            this.dialog = false
        }
    }
  }
</script>