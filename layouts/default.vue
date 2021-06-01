<template >
  <v-app :style="{ background: $vuetify.theme.themes[theme].background }">
    <v-main>
      <v-app-bar color="primary" app dark>
        <v-app-bar-nav-icon>
          <v-btn icon nuxt href="/"><v-icon>mdi-home</v-icon></v-btn>
        </v-app-bar-nav-icon>
        <v-toolbar-title > Iscas de Fly </v-toolbar-title>
        <v-spacer></v-spacer>
        <v-btn icon nuxt href="/post"> Blog </v-btn>
        <v-btn
          icon
          target="_blank"
          href="https://www.instagram.com/explore/tags/pescacommosca/"
        >
          <v-icon>mdi-instagram</v-icon>
        </v-btn>
      </v-app-bar>
      <v-container fluid>
        <nuxt />
      </v-container>
    </v-main>
    <v-footer absolute elevation="10" padless app color="primary">
      <v-col class="white--text text-center py-1">Zero / Dez - Fry Fishing  &copy; {{ new Date().getFullYear() }}</v-col>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      title: 'Vuetify.js',
    }
  },
  computed: {
    theme() {
      return this.$vuetify.theme.dark ? 'dark' : 'light'
    },
  },
}
</script>
<style>
</style>
