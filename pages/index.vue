<template>
  <v-container>
    <v-row  justify="center">
      <h1 class="text-h2 primary--text">
        <span class="text-h4 d-none d-sm-inline">www.</span>
        Iscas de Fly
        <span class="text-h4 d-none d-sm-inline">.com.br</span>
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
          <PostDestaque :postsDestaque="posts"></PostDestaque>
        </v-col>
      </v-row>
    </v-container>
  
</template>

<script>
import axios from 'axios'
export default {
  asyncData({ params }) {
    return axios(
      `https://iscasdefly.000webhostapp.com/wp-json/wp/v2/posts?per_page=3`
    )
      .then((response) => {
        return { posts: response.data }
      })
      .catch((error) => {
        return { error: error }
      })
  },
  data() {
    return {
      posts: [],
      error: [],
    }
  },
}
</script>
