<template>
  <div>
    <v-dialog
      v-model="dialog"
      width="400"
    >
      <template v-slot:activator="{ on }">
        <v-btn
          class="success darken-1 white--text"
          v-on="on"
          style="height: 48px"
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
          <v-form class="px-3 pt-3" ref="form">
              <v-text-field id="addTodoInput" title="Title" v-model="title" label="title" :rules="inputRules" class="mb-3"></v-text-field>
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
        if (this.$refs.form.validate()) {
          const newTodo = {
              title: this.title,
              completed: false,
          }
          this.$emit('add-todo', newTodo)
          this.dialog = false
        }     
      }
    }
  }
</script>