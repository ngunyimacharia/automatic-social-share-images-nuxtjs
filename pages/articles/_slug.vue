<template>
  <div>
    <article-render :article="article" />
    <more-articles :articles="articles" />
  </div>
</template>

<script>
import ArticleRender from "../../components/ArticleRender.vue";

import MoreArticles from "../../components/MoreArticles.vue";

export default {
  components: {
    ArticleRender,
    MoreArticles,
  },

  async asyncData({ $content, params }) {
    const article = await $content("articles", params.slug).fetch();

    const articles = await $content("articles")
      .where({
        slug: { $ne: params.slug },
      })
      .fetch();

    return {
      article,
      articles,
    };
  },
};
</script>