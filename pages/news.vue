<template>
  <div>
    <v-container>
      <v-flex xs12 pb-3>
        <h2>News</h2>
      </v-flex>
      <v-flex v-for="(article, index) in articles" :key="index">
        <v-card class="mx-auto" max-width="350">
          <img :src="article.urlToImage" width="100%" height="250px" />
          <v-card-title> {{ article.title }} </v-card-title>
          <v-divider></v-divider>
          <v-card-text>
            {{ article.description }}
          </v-card-text>
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn flat :href="article.url" target="_blank">Link</v-btn>
          </v-card-actions>
        </v-card>
      </v-flex>
    </v-container>
  </div>
</template>

<script>
export default {
  async asyncData({ app }) {
    const { articles } = await app.$axios.$get(
      'https://newsapi.org/v2/top-headlines?sources=techcrunch&apiKey=dbccf410f7cc4a22a178086ed6cffc83'
    )
    return { articles }
  },
}
</script>

<style></style>
