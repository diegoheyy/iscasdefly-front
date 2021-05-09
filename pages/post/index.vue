<template>
  <vcontainer>
    <theListPost :posts="posts"></theListPost>
  </vcontainer>
</template>
<script>
import axios from 'axios'
import theListPost from '../../components/theListPost.vue'
export default {
  components: { theListPost },
  asyncData({ params }) {
    return axios(`https://iscasdefly.000webhostapp.com/wp-json/wp/v2/posts`)
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