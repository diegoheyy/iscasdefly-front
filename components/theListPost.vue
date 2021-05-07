<template>
  <v-container class="pa-1">
    <v-data-iterator :items="posts" :search="search" hide-default-footer>
      <template v-slot:header>
        <v-toolbar dark color="blue darken-3" class="mb-1">
          <v-text-field
            v-model="search"
            clearable
            flat
            solo-inverted
            hide-details
            prepend-inner-icon="mdi-magnify"
            label="Search"
          ></v-text-field>
        </v-toolbar>
      </template>
      <template v-slot:default="{ items }">
        <v-row>
          <v-col v-for="(post, i) in posts" :key="i" cols="12" md="6">
            <v-card class="" max-width="600">
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
              <v-card-actions>
                <v-spacer></v-spacer
                ><v-btn text color="primary" small>
                  Ler Mais
                  <v-icon right dark> mdi-arrow-right </v-icon>
                </v-btn></v-card-actions
              >
            </v-card>
          </v-col>
        </v-row>
      </template>
    </v-data-iterator>
    <!-- <v-col v-for="(post, i) in posts" :key="i" cols="12" lg="4" md="6">
            <v-card class="mx-auto" max-width="600">
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
              <v-card-actions>
                <v-spacer></v-spacer
                ><v-btn text color="primary" small>
                  Ler Mais
                  <v-icon right dark> mdi-arrow-right </v-icon>
                </v-btn></v-card-actions
              >
            </v-card>
          </v-col> -->
  </v-container>
</template>
<script>
import axios from 'axios'
export default {
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
