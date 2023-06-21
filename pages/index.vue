<script>
import Header from "@/components/Header.vue";
import Hero from "@/components/Hero.vue";
import Article from "@/components/CardArticle.vue";
export default {
  components: {
    Header,
    Hero,
    Article,
  },
  data() {
    return {
      articles: [],
    };
  },
  async fetch() {
    await this.$axios
      .get("v1/cnn-news")
      .then((res) => (this.articles = res.data.data));
  },
};
</script>

<template>
  <div id="app">
    <Header />
    <main class="container">
      <Hero />
      <div class="row mb-2">
        <Article
          v-for="(article, index) in articles"
          :key="index"
          :article="article"
        />
      </div>
    </main>
  </div>
</template>
