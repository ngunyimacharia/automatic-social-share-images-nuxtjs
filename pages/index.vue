<template>
  <div>
    <article-render :article="article" />
    <more-articles :articles="articles" />
  </div>
</template>

<script>
import ArticleRender from "../components/ArticleRender.vue";

import MoreArticles from "../components/MoreArticles.vue";

export default {
  components: {
    ArticleRender,
    MoreArticles,
  },

  async asyncData({ $content }) {
    const articles = await $content("articles").fetch();

    const article = articles.pop();

    return {
      article,
      articles,
    };
  },
};
</script>