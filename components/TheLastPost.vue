<template>
  <v-carousel
    cycle
    :show-arrows-on-hover="true"
    :hide-delimiter-background="false"
    delimiter-icon="mdi-fish"
    height="400"
  >
    <v-carousel-item v-for="post in postsDestaque" :key="post.id">
      <template v-slot>
        <v-row fluid>
          <v-col md="9" class="px-0">
            <v-img
              height="400"
              position="center"
              :src="post.featured_image_url"
            >
            </v-img>
          </v-col>
          <!-- :visible="$vuetify.breakpoint.mobile" -->
          <v-col  md="3" class="align-stretch white">
            <v-card-title
              class="primary--text title"
              v-text="post.title.rendered"
            ></v-card-title>
          </v-col>
        </v-row>
      </template>
    </v-carousel-item>
  </v-carousel>
</template>

<script>
// import axios from 'axios'

export default {
  name: 'TheLastPost',
  props: {
    postsDestaque: {
      type: Array,
      required: false,
    },
  },
  data() {
    return {}
  },
  methods: {
    noReadMore(text) {
      return text.substr(0, text.indexOf('</p>') + 4)
    },
  },
}
</script>

<style>
</style>
