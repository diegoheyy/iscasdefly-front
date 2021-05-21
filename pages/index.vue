<template>
  <v-container>
    <v-row justify="center">
      <h1 class="text-h2 primary--text">
        <!-- <span class="text-h4 d-none d-sm-inline">www.</span> -->
        Iscas de Fly
        <!-- <span class="text-h4 d-none d-sm-inline">.com.br</span> -->
      </h1>
    </v-row>
    <v-row justify="center">
      <div class="text-body-2 subtitle mt-5">
        Um Blog sobre o mundo do Fly Fishing e as maravilhas da pesca.
      </div>
    </v-row>
    <v-row justify="center"><v-divider></v-divider></v-row>

    <v-row justify="center" class="mt-5">
      <v-col lg="12" md="10">
        <TheLastPost :postsDestaque="postDestaque"></TheLastPost>
      </v-col>
    </v-row>
    <v-row justify="center" class="mt-5">
      <v-col lg="12" md="10">
        <TheListPost :posts="post"></TheListPost>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios'
export default {
  
  asyncData({ params }) {
    return axios.all([
      axios.get(`${process.env.BASE_API}/posts?per_page=5&_embed`),
      axios.get(`${process.env.BASE_API}/posts?per_page=12&_embed`)])
      .then(axios.spread((response, response1) => {
        return { 
          postDestaque: response.data,
          post: response1.data,
          }
                  
      }))
      .catch((error) => {
        return { error: error }
      })
  },
  data() {
    return {
      postDestaque: [],
      post: [],
      error: [],
      page: 1,
    }
  },
}
</script>
