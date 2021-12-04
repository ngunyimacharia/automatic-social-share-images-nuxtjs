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

  data() {
    return {
      icons: {
        globe:
          "https://res.cloudinary.com/kmashytski/image/upload/v1624938606/business-card-generator/assets/globe-icon.png",
        logo: "https://res.cloudinary.com/kmashytski/image/upload/v1624939714/business-card-generator/assets/logo-icon.png",
        mail: "https://res.cloudinary.com/kmashytski/image/upload/v1624938364/business-card-generator/assets/mail-icon.png",
        pin: "https://res.cloudinary.com/kmashytski/image/upload/v1624937477/business-card-generator/assets/pin-icon.png",
        smartphone:
          "https://res.cloudinary.com/kmashytski/image/upload/v1624937998/business-card-generator/assets/smartphone-icon.png",
      },
    };
  },
};
</script>