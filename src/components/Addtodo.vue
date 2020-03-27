<template>
  <div>
      <v-form>
          <v-container>
              <v-row>
                  <v-col cols="12" md="4">
                      <v-text-field
                        v-model="firstname"
                        :rules="nameRules"
                        :counter="20"
                        label="Todo title"
                        required
                      ></v-text-field>
                  </v-col>
              </v-row>
          </v-container>
      </v-form>
  </div>
</template>

<script>
export default {

}
</script>

<style>

</style>