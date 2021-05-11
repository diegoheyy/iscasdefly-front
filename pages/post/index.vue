<template>
  <vcontainer>
    <TheListPost :posts="posts"></TheListPost>
  </vcontainer>
</template>
<script>
import axios from 'axios'
export default {
  

  asyncData({ params } ) {
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