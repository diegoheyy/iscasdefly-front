<template>
<v-slot ></v-slot>
</template>
   
<script>

import axios from 'axios'
export default {
  name: 'TheListPost',
  props: {
    posts: Array,
  },

  data() {
    return {
      error: [],
      search: '',
    }
  },
  methods: {
    noReadMore(text) {
      return text.substr(0, text.indexOf('</p>') + 4)
    },
  },
}
</script>
<style scoped>

</style>
