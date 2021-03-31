<template>
  <v-app id="inspire">
    <v-navigation-drawer permanent v-if="drawer" app>
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="title">
            {{ $store.state.appTitle }}
          </v-list-item-title>
        </v-list-item-content>
      </v-list-item>

      <v-divider></v-divider>

      <v-list
        dense
        nav
      >
        <v-list-item
          v-for="item in items"
          :key="item.title"
          :to="item.to"
          link
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

    <v-app-bar
      app
      color="#fcb69f"
      dark
      src="banner.jpg"
      prominent
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-container>
        <v-row>
          <v-app-bar-nav-icon @click="drawer = !drawer"></v-app-bar-nav-icon>
          <v-app-bar-title>{{ $store.state.appTitle }}</v-app-bar-title>
        </v-row>
        <v-row>
          <LiveDateTime />
        </v-row>
      </v-container>

      <v-spacer></v-spacer>

      <Search />

    </v-app-bar>

    <v-main>
      <router-view></router-view>
      <Snackbar/>
    </v-main>
  </v-app>
</template>

<script>
  import Snackbar from '@/components/Shared/Snackbar.vue'
  import Search from '@/components/Tools/Search.vue'
  import LiveDateTime from '@/components/Tools/LiveDateTime.vue'

  export default {
    components: { Snackbar, Search, LiveDateTime },
    data: () => ({ 
      drawer: null,
      items: [
        { title: 'Todo', icon: 'mdi-format-list-checks', to: '/' },
        { title: 'About', icon: 'mdi-help-box', to: '/about' },
      ], 
    }),
  }
</script>