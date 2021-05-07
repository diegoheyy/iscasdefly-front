<template>
  <section class="container">
    <div>
      <h1 class="title">
        {{post.title.rendered}}
      </h1>
      <span v-html="post.content.rendered"></span>
    </div>
  </section>
</template>
<script>
import axios from 'axios'
export default {
   head () {
    return {
      title: this.post._yoast_wpseo_title,
      meta: [
        { hid: 'description', id: 'description', name: 'description', content: this.post._yoast_wpseo_metadesc }
      ]
    }
  },
  asyncData ({ params }) {
    return axios.get(`http://localhost/wordpress/wp-json/wp/v2/posts/${params.id}`)
      .then(response => {
        return { post: response.data }
      })
      .catch((error) => {
        return { error: error }
      })
  },
  data () {
    return {
      post: {},
      error: []
    }
  }
}
</script>
<style>
.container {
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  /* text-align: center; */
}
.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}
</style>