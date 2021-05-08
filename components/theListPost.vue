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
            label="O que está procurando ?"
          ></v-text-field>
        </v-toolbar>
      </template>
      <template v-slot:default="props">
        
        <v-row justify="space-around mt-5">
          <v-col v-for="(post) in props.items" :key="post" cols="12" md="6" lg="4">
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
<style>

.truncate-overflow{
  --max-lines: 3;
  position: relative;
  max-height: calc(var(--lh) * var(--max-lines));
  overflow: hidden;
  padding-right: 1rem; /* space for ellipsis */
}
.truncate-overflow::before {
  position: absolute;
  content: "...";
  /* tempting... but shows when lines == content */
  /* top: calc(var(--lh) * (var(--max-lines) - 1)); */
  
  /*
  inset-block-end: 0;
  inset-inline-end: 0;
  */
  bottom: 0;
  right: 0;
}
.truncate-overflow::after {
  content: "";
  position: absolute;
  /*
  inset-inline-end: 0;
  */
  right: 0;
  /* missing bottom on purpose*/
  width: 1rem;
  height: 1rem;
  background: white;
}
</style>
