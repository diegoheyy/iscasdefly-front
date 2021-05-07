<template>
  <vcontainer>
<<<<<<< HEAD
    <v-btn color="primary" elevation="2" large>ALOW</v-btn>
    <v-container class="pa-1">
      <v-item-group>
        <v-row>
          <v-col v-for="(post, i) in posts" :key="i" cols="12" md="6">
            <v-img :src="`${post.fimg_url}`" height="150"></v-img>
            <v-item>
              {{ post.title.rendered }}
            </v-item>
          </v-col>
        </v-row>
      </v-item-group>
    </v-container>
=======
    <theListPost :posts="posts"></theListPost>
>>>>>>> 8f38ac0cee78953a955f2fd7c08ad78e9f6a5c28
  </vcontainer>
</template>
<script>
import axios from 'axios'
import theListPost from '../../components/theListPost.vue'
export default {
  components: { theListPost },
  asyncData({ params }) {
<<<<<<< HEAD
    return axios(`http://localhost/wordpress/wp-json/wp/v2/posts`)
=======
    return axios(`https://iscasdefly.000webhostapp.com//wp-json/wp/v2/posts`)
>>>>>>> 8f38ac0cee78953a955f2fd7c08ad78e9f6a5c28
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