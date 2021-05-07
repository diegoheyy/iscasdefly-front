<template class="working">
  <vcontainer>
    <v-btn color="primary" elevation="2" large>ALOW</v-btn>
    <v-container class="pa-1">
      <v-item-group>
        <v-row>
          <v-col v-for="(post, i) in posts" :key="i" cols="12" lg="4" md="6">
            <v-card class="mx-auto"
        max-width="600"
        >
              <v-img
                :src="`${post.featured_image_url}`"
                class="white--text align-end"
                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                height="250"
              >
                <v-card-title v-text="post.title.rendered"></v-card-title>
              </v-img>
              <v-card-subtitle 
                v-html="noReadMore(post.excerpt.rendered)"
              ></v-card-subtitle>
              <v-card-actions> <v-spacer></v-spacer><v-btn
    
                     text
                    color="primary"
                    small
                  >
                  
                    Ler Mais
                    <v-icon
        right
        dark
      >
        mdi-arrow-right
      </v-icon>
                  </v-btn></v-card-actions>
            </v-card>
          </v-col>
        </v-row>
      </v-item-group>
    </v-container>
  </vcontainer>
</template>
<script>
import axios from 'axios'
export default {
  props: {
    posts: Array,
  },

  data() {
    return {
      posts: {},
      error: [],
    }
  },
  methods: {
    noReadMore(text) {
      return text.substr(0, text.indexOf('</p>') + 4)
    },
  },
}
</script>
