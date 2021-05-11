<template>
  <v-container class="">
    <v-row justify="center" class="mt-n16">
      <v-avatar size="96">
        <img :src="author.avatar_urls['96']" :alt="author.name" />
      </v-avatar>
    </v-row>
    <v-row justify="center">
      <v-col md="8" class="text-center">{{ author.description }}</v-col>
    </v-row>
    <v-row justify="center">
      <v-btn icon @click="author.url">
        <v-icon class="mr-2">mdi-instagram</v-icon>
        {{ author.name }}
      </v-btn>
    </v-row>
  </v-container>
</template>
<script>
import axios from 'axios'
export default {
  props: {
    author: {},
  },

  data() {
    return {
      error: [],
    }
  },
}
</script>
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Lato&family=Quicksand&display=swap');
.contentPost {
  font-family: 'Quicksand', sans-serif;
}
.tituloPost {
  font-family: 'Lato', sans-serif;
}
</style>