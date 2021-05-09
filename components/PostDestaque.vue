<template>
  <v-carousel
    cycle
    :show-arrows-on-hover="true"
    :hide-delimiter-background="false"
    delimiter-icon="mdi-fish"
    height="400"
  >
    <v-carousel-item v-for="post in postsDestaque" :key="post.id">
      <v-row>
        <v-col md="9">
      <v-img height="400" position="center" :src="post.featured_image_url"></v-img>

        </v-col>
        <v-col md="3"></v-col>

      </v-row>
    </v-carousel-item>
  </v-carousel>
</template>

<script>
// import axios from 'axios'

export default {
  name: 'PostDestaque',
  props: {
    postsDestaque: {
      type: Array,
      required: false,
    },
  },
  data() {
    return {}
  },
}
</script>

<style>
</style>
