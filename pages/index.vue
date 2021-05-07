<template>
<<<<<<< HEAD
  <div>
    <div class="container">
      <div>
        <h1 class="text-h2 primary--text">
          <span class="text-h4 d-none d-sm-inline">www.</span>
          Iscas de Fly
          <span class="text-h4 d-none d-sm-inline">.com.br</span>
        </h1>
        <div class="text-body-2 subtitle mt-5">
          Um Blog sobre o mundo do Fly Fishing e as maravilhas da pesca.
        </div>
        <!-- <div class="links">
          <v-btn color="primary" outlined small nuxt href="/post"> Blog </v-btn>
          <v-btn
            color="primary"
            outlined
            small
            target="_blank"
            href="https://www.instagram.com/explore/tags/pescacommosca/"
          >
            Instagram <v-icon>mdi-instagram</v-icon>
          </v-btn>
        </div> -->
        <v-divider></v-divider>
        <container>
          <v-row justify="center" class="mt-5">
           
            <v-col col="10">
              <PostDestaque :postsDestaque="posts"></PostDestaque>
            </v-col>
           
          </v-row>
          <!-- <v-carousel>
            <v-carousel-item
              v-for="post in postsDestaque"
              :key="post.id"
              :src="post.fimg_url"
            >
              <div class="display-3">{{ post.i }} Slide</div></v-carousel-item
            >
          </v-carousel> -->
        </container>
=======
  <div class="container">
    <div>
      <h1 class="text-h2 primary--text">
        <span class="text-h4 d-none d-sm-inline">www.</span>Iscas de Fly<span
          class="text-h4 d-none d-sm-inline">.com.br</span
        >
      </h1>
      <div class="text-body-2 subtitle mt-5">
        Em breve um Blog sobre o mundo do Fly Fishing e as maravilhas da pesca.
      </div>
      <div class="links">
        <v-btn color="primary" outlined small nuxt href="/post"> Blog </v-btn>
        <v-btn
          color="primary"
          outlined
          small
          target="_blank"
          href="https://www.instagram.com/explore/tags/pescacommosca/"
        >
          Instagram <v-icon>mdi-instagram</v-icon>
        </v-btn>
>>>>>>> 8f38ac0cee78953a955f2fd7c08ad78e9f6a5c28
      </div>
    </div>
  </div>
</template>

<script>
import axios from 'axios'
export default {
  asyncData({ params }) {
    return axios(`http://localhost/wordpress/wp-json/wp/v2/posts?per_page=3`)
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

<style>
.container {
  margin: 0 auto;
  min-height: 50vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 250px !important;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
