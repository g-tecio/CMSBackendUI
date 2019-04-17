<template>
<nav>
     <v-toolbar  color="white"
      flat
      app
     >
    <v-toolbar-side-icon @click="drawer = !drawer" />

    <v-toolbar-title class="white--text"></v-toolbar-title>

    <v-spacer></v-spacer>

    <v-btn icon>
      <v-icon>search</v-icon>
    </v-btn>

    <v-btn icon>
      <v-icon>apps</v-icon>
    </v-btn>

    <v-btn icon>
      <v-icon>refresh</v-icon>
    </v-btn>

    <v-btn icon>
      <v-icon>more_vert</v-icon>
    </v-btn>
  </v-toolbar>

    <v-navigation-drawer
    class="deep-purple darken-1"
    dark
    v-model="drawer"
    app
  >
    <v-list>
        <v-list-tile>
          <v-list-tile-title class="title">
            El General
          </v-list-tile-title>
        </v-list-tile>
        <v-divider/>
      <v-list-tile
        v-for="item in items"
        :key="item.title"
      >
        <v-list-tile-action>
          <v-icon>{{ item.icon }}</v-icon>
        </v-list-tile-action>

        <v-list-tile-content>
          <router-link :to="item.to"><v-list-tile-title>{{ item.title }}</v-list-tile-title></router-link>
        </v-list-tile-content>
      </v-list-tile>
    </v-list>
  </v-navigation-drawer>

</nav>
</template>

<script>
export default {
data() {
    return {
      drawer: false,
      items: [
        {
          icon: 'home',
          title: 'Home',
          to: '/'
        },
        
        {
          icon: 'bar_chart',
          title: 'Dashboard',
          to: '/'
        },
        {
          icon: 'memory',
          title: 'Metadata',
          to: '/'
        },
        {
          icon: 'table_chart',
          title: 'Structure Content',
          to: '/structure-content'
        },
        {
          icon: 'settings',
          title: 'Settings',
          to: '/'
        }
      ]
    }
  }
}
</script>

<style>

</style>
