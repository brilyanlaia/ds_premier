<template>
  <v-card class="rounded-0">
    <v-layout>
      <!-- <v-system-bar color="deep-purple darken-3"></v-system-bar> -->

      <v-app-bar
        color="primary"
        prominent
      >
        <v-app-bar-nav-icon variant="text" @click.stop="drawer = !drawer"></v-app-bar-nav-icon>

        <v-toolbar-title>Dashboard</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn variant="text" icon="mdi-magnify"></v-btn>

        <v-btn variant="text" icon="mdi-filter"></v-btn>

        <v-btn variant="text" icon="mdi-dots-vertical"></v-btn>
      </v-app-bar>

      <v-navigation-drawer
        v-model="drawer"
        bottom
        app
      >
        <!-- <v-list
           :items="items"
        ></v-list> -->
        <v-list>
            <v-list-item
          v-for="i in items"
          :to="i.value"
          :key="i"
          link
          active-class="active-link"
          class="rounded"
        >
          <v-list-item-content>
            <v-list-item-title>
              {{ i.title }}
            </v-list-item-title>
          </v-list-item-content>
        </v-list-item>
        </v-list>
      </v-navigation-drawer>

      <v-main>
        <router-view></router-view>
      </v-main>
    </v-layout>
  </v-card>
</template>

<script>
  export default {
    data: () => ({
      drawer: false,
      group: null,
      items: [
        {
          title: 'Home',
          value: '/dashboard',
        },
        {
          title: 'Dummy',
          value: '/dashboard/dummy',
        },
      ],
    }),

    watch: {
      group () {
        this.drawer = false
      },
    },
  }
</script>

<style>
 .v-main{
    background: #f2f3f7 !important;
    height: 100vh;
  }
  .v-app-bar.v-toolbar{
     background: #111827 !important;
     color: #f2f3f7 !important;
  }
  .v-navigation-drawer{
    background: #111827 !important;
    color: white !important;
  }
  .active-link{
    background-color: #2196f321 !important;
    color: #1e89de !important;
  }
</style>
