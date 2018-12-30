<template>
  <v-app>
    <v-navigation-drawer
      :clipped="clipped"
      v-model="drawer"
      fixed
      app
    >
      <v-list>
        <v-list-tile
          v-for="(item, i) in items"
          :to="item.to"
          :key="i"
          router
          exact
        >
          <v-list-tile-action>
            <v-icon v-html="item.icon" />
          </v-list-tile-action>
          <v-list-tile-content>
            <v-list-tile-title v-text="item.title" />
          </v-list-tile-content>
        </v-list-tile>
      </v-list>
    </v-navigation-drawer>
    <v-toolbar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-toolbar-side-icon @click="drawer = !drawer" />
      <nuxt-link :to="'/'">
        <img 
          src="https://res.cloudinary.com/filosofikode/image/upload/v1546074073/logo-filosofi-kode-square-transparent-48-48.png" 
          alt="Logo Filosofi Kode">
      </nuxt-link>
      <nuxt-link 
        :to="'/'"
        style="text-decoration: none;">
        <v-toolbar-title 
          class="hidden-xs-only pt-2 pl-2"
          v-text="title" />

      </nuxt-link>
      <v-spacer />
      <v-btn icon>
        <v-icon>search</v-icon>
      </v-btn>
      <v-btn icon>
        <v-icon>more_vert</v-icon>
      </v-btn>
    </v-toolbar>
    <v-content>
      <v-container>
        <v-layout
          column
          justify-center
          align-center
        >
          <v-flex
            xs12
          >
            <nuxt />
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
    <v-footer app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: true,
      drawer: false,
      items: [
        { icon: 'apps', title: 'Welcome', to: '/' },
        { icon: 'bubble_chart', title: 'Inspire', to: '/inspire' }
      ],
      right: true,
      title: 'Filosofi Kode'
    }
  }
}
</script>
