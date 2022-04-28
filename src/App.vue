<template>
  <v-app id="inspire">

    <v-navigation-drawer
      v-model="drawer"
      :mobile-breakpoint="768"
      app
    >
      <v-img
      class="pa-4"
        height="150"
        src="clouds.png"
        gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
      >
        <v-avatar size="70" class="mb-2">
          <img
            src="Nick-logo.png"
            alt="Nick"
          >
        </v-avatar>
        <div class="white--text text-subtitle-1 font-weight-bold">
          Nick Ned
        </div>
        <div class="white--text text-subtitle-2">
          MrNedNick
        </div>
      </v-img>

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
      color="primary"
      src="clouds.png"
      app
      dark
      prominent
      height="150"
    >
      <template v-slot:img="{ props }">
        <v-img
          v-bind="props"
          gradient="to top right, rgba(19,84,122,.5), rgba(128,208,199,.8)"
        ></v-img>
      </template>

      <v-container class="header-container pa-0">
        <v-row>
          <v-app-bar-nav-icon 
            @click="drawer = !drawer" 
          />
          <v-spacer />
          <search />
        </v-row>
        <v-row>
          <v-toolbar-title class="ml-4 text-h4">
            {{ $store.state.appTitle }}
          </v-toolbar-title>
        </v-row>
        <v-row>
          <live-date-time />
        </v-row>
      </v-container>

    </v-app-bar>

    <v-main>
      <router-view></router-view>
      <snackbar />
    </v-main>
  </v-app>
</template>

<script>

  export default {
    data: () => ({ 
      drawer: null,
      items: [
          { title: 'Todo', icon: 'mdi-format-list-checks', to: '/' },
          { title: 'About', icon: 'mdi-help-box', to: '/about' },
        ],
    }),
    mounted() {
      this.$store.dispatch('getTasks')
    },
    components: {
      'search': require('@/components/Tools/Search.vue').default,
      'live-date-time': require('@/components/Tools/LiveDateTime.vue').default,
      'snackbar': require('@/components/Shared/Snackbar.vue').default
    }
  }
</script>

<style lang="sass">
  .header-container
    max-width: none !important
</style>