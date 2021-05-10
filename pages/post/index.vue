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
  asyncData({ params } ) {
    console.log(process.env.BASE_API)
    return axios(
      `${process.env.BASE_API}/posts?per_page=99`
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