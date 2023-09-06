<template>
  <v-app id="inspire">
    <v-navigation-drawer v-model="drawer" theme="dark">
      <v-list nav>
        <v-list-item prepend-icon="mdi-mastodon" title="Todo" value="Todo" to="home"></v-list-item>
        <v-list-item prepend-icon="mdi-account-supervisor-circle" title="About" value="About" to="about"></v-list-item>
      </v-list>
    </v-navigation-drawer>

      <v-app-bar color="teal-darken-4" image="https://picsum.photos/1920/1080?random">
        <template v-slot:image>
            <v-img gradient="to top right, rgba(19,84,122,.8), rgba(128,208,199,.8)"></v-img>
        </template>

        <template v-slot:prepend>
            <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
        </template>

        <v-app-bar-title >Title</v-app-bar-title>

        <v-spacer></v-spacer>

        <v-btn icon>
            <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
            <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
            <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
    </v-app-bar>

    <v-main>
      <router-view></router-view>
    </v-main>
  </v-app>
</template>

<script setup>
import { ref } from 'vue'

const drawer = ref(null)
</script>

<script>
export default {
  data: () => ({ drawer: null }),
}
</script>