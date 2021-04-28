<template>
  <vcontainer>
    <v-btn color="primary" elevation="2" large>ALOW</v-btn>
    <v-container class="pa-1">
      <v-item-group>
        <v-row>
          <v-col v-for="(post, i) in posts" :key="i" cols="12" md="6">
            <v-img :src="`${post.fimg_url}`"  height="150" ></v-img>
            <v-item >
                     {{post.title.rendered}}
            </v-item>
          </v-col>
        </v-row>
      </v-item-group>
    </v-container>
  </vcontainer>
</template>
<script>
import axios from 'axios'
export default {
  asyncData({ params }) {
    return axios(`https://barradois.com/wp-json/wp/v2/posts`)
      .then((response) => {
        return { posts: response.data }
      })
      .catch((error) => {
        return { error: error }
      })
  },
  data() {
    return {
      posts: {},
      error: [],
    }
  },
}
</script>