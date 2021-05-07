<template>
  <v-carousel
    cycle
    :show-arrows-on-hover="false"
    hide-delimiter-background
    delimiter-icon="mdi-fish"
  >
    <v-carousel-item
      v-for="post in postsDestaque"
      :key="post.id"
      :src="post.fimg_url"
      width="800px"
    >
      <v-row style="height: 100%" no-gutters align="end">
        <v-col align-self="start" md="8">
          <div class="display-1 blue darken-1 pa-2 white--tex elevation-3">
            {{ post.title.rendered }}
          </div>
        </v-col>
        <!-- <v-spacer></v-spacer> -->
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
  //   asyncData({ params }) {
  //     return axios(`http://localhost/wordpress/wp-json/wp/v2/posts`)
  //       .then((response) => {
  //         return { posts: response.data }
  //       })
  //       .catch((error) => {
  //         return { error: error }
  //       })
  //   },
  data() {
    return {}
  },
}
</script>

<style>
</style>
