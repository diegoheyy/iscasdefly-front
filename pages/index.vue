<template>
  <div class="container">
    <div>
      <h1 class="text-h2 primary--text">
        <span class="text-h4 d-none d-sm-inline">www.</span>Iscas de Fly<span
          class="text-h4 d-none d-sm-inline">.com.br</span
        >
      </h1>
      <div class="text-body-2 subtitle mt-5">
        Em breve um Blog sobre o mundo do Fly Fishing e as maravilhas da pesca.
      </div>
      <div class="links">
        <!-- <v-btn color="primary" outlined small nuxt href="/post"> Blog </v-btn> -->
        <v-btn
          color="primary"
          outlined
          small
          target="_blank"
          href="https://www.instagram.com/explore/tags/pescacommosca/"
        >
          Instagram <v-icon>mdi-instagram</v-icon>
        </v-btn>
      </div>
    </div>
  </div>
</template>

<script>
export default {}
</script>

<style>
.container {
  margin: 0 auto;
  min-height: 90vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 250px !important;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
