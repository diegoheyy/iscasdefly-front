<template>
  <v-container>
    <section>
      <v-card class="pa-5">
        <v-row align="center" justify="center">
          <v-col col="6" class="text-center display-3 titulo-post">
            {{ post.title.rendered }}
          </v-col>
        </v-row>
        <v-row>
          <v-divider></v-divider>
        </v-row>
        <v-row v-if="post.featured_image_url">
          <v-img
            height="60vh"
            max-height="450px"
            :src="post.featured_image_url"
            alt=""
          >
          </v-img>
        </v-row>
        <v-row justify="center">
          <v-col md="8">
            <PostConstent>
              <div class="contentPost" v-html="post.content.rendered"></div>
            </PostConstent>
          </v-col>
        </v-row>

        <v-row class="mt-12">
          <v-divider></v-divider>
        </v-row>
        <v-row>
          <TheAuthor :author="post._embedded.author[0]"></TheAuthor>
        </v-row>
      </v-card>
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
    return axios(`${process.env.BASE_API}/posts/${params.id}?_embed`)
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
<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Lato&family=Quicksand&display=swap');
.contentPost {
  font-family: 'Quicksand', sans-serif;
}
.tituloPost {
  font-family: 'Lato', sans-serif;
}

.contentPost >>> img {
  max-width: 100%;
  height: auto;
  max-height: 1200px;
  display: block;
  margin-left: auto;
  margin-right: auto;
}
.contentPost >>> p {
  text-align: justify;
}
</style>