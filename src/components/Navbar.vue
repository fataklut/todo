<template>
  <v-sheet>
    <nav>
      <v-app-bar class="purple absolute temporary" flat app> 
        <v-app-bar-nav-icon class="white--text" @click="drawer = !drawer"></v-app-bar-nav-icon>
      </v-app-bar>
    </nav>

    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
    >
      <v-list-item>
        <v-list-item-avatar>
          <v-img src="https://scontent.fkix2-1.fna.fbcdn.net/v/t1.0-1/p320x320/81280327_3440291709378108_3170576382967152640_o.jpg?_nc_cat=104&_nc_sid=7206a8&_nc_ohc=eIpEH9cWAsYAX_P3dpn&_nc_ht=scontent.fkix2-1.fna&_nc_tp=6&oh=3bc9ca199d17f09bf63e3c74bf20ac2a&oe=5EA45188"></v-img>
        </v-list-item-avatar>

        <v-list-item-content>
          <v-list-item-title>Andreas Houg</v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>

        <v-list-item
          v-for="item in items" :key="item.title" router :to="item.route"
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <v-list-item-title>{{ item.title }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-sheet>
</template>

<script>
export default {
  data() {
    return {
      drawer: false,
      items: [
          { title: 'Home', icon: 'dashboard', route: '/' },
          { title: 'About', icon: 'question_answer', route: '/about'},
        ],
    }
  }
}
</script>

<style>

</style>