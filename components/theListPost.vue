<template>
  <v-container class="pa-1">
    <v-data-iterator :items="posts" :search="search" hide-default-footer disable-pagination>
      <template v-slot:header>
        <v-toolbar fixed  dark color="primary" class="mb-1">
          <v-text-field
            v-model="search"
            clearable
            flat
            fluid
            solo-inverted
            hide-details
            prepend-inner-icon="mdi-magnify"
            label="O que está procurando ?"
          ></v-text-field>
        </v-toolbar>
      </template>
      <template v-slot:default="props">
        
        <v-row justify="space-around mt-4">
          <v-col v-for="(post) in props.items" :key="post.title.rendered" cols="12" md="6" lg="4">
            <v-card class="">
              <v-img
                :src="`${post.featured_image_url}`"
                class="white--text align-end"
                gradient="to bottom, rgba(0,0,0,.1), rgba(0,0,0,.5)"
                height="250"
              >
                <v-card-title v-text="post.title.rendered"></v-card-title>
              </v-img>
              <v-card-text
                class="overflow-hidden"
                v-html="noReadMore(post.excerpt.rendered)"
                
              ></v-card-text>
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
