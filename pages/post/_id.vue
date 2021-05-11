<template>
  <v-container>
    <v-card elevation="0">
     <v-card outlined primary class="mt-n3">
      <v-text class="display-4">
        {{ post.title.rendered }}
      </v-text>
    </v-card>
    </v-card>
    
    <v-img height="60vh" :src="post.featured_image_url"> </v-img>
   
    <section>
      <v-card class="pa-5">
        <PostConstent>
          <div v-html="post.content.rendered"></div>
        </PostConstent>
      </v-card>

      <div>
        <h1 class="title">
          {{ post.title.rendered }}
        </h1>
      </div>
    </section>
  </v-container>
</template>
<script>
import axios from 'axios'
export default {
  head() {
    return {
      title: this.post._yoast_wpseo_title,
      meta: [
        {
          hid: 'description',
          id: 'description',
          name: 'description',
          content: this.post._yoast_wpseo_metadesc,
        },
      ],
    }
  },
  asyncData({ params }) {
    return axios
      .get(`${process.env.BASE_API}/posts/${params.id}`)
      .then((response) => {
        return { post: response.data }
      })
      .catch((error) => {
        return { error: error }
      })
  },
  data() {
    return {
      post: {},
      error: [],
    }
  },
}
</script>
<style>
</style>