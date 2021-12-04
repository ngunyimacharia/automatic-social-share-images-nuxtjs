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

  head() {
    return {
      meta: [
        { property: "og:site_name", content: "NuxtJs Blog" },

        { hid: "og:type", property: "og:type", content: "article" },

        {
          hid: "og:url",
          property: "og:url",
          content: process.env.NUXT_ENV_URL,
        },

        {
          hid: "og:title",
          property: "og:title",
          content: this.article.title,
        },

        {
          hid: "og:description",
          property: "og:description",
          content: this.article.description,
        },

        {
          hid: "og:image",
          property: "og:image",
          content: this.ogImageUrl,
        },

        { property: "og:image:width", content: "1200" },

        { property: "og:image:height", content: "630" },

        { name: "twitter:site", content: "NuxtJs Blog" },

        { name: "twitter:card", content: "summary_large_image" },

        {
          hid: "twitter:url",
          name: "twitter:url",
          content: process.env.NUXT_ENV_URL,
        },

        {
          hid: "twitter:title",
          name: "twitter:title",
          content: this.article.title,
        },

        {
          hid: "twitter:description",
          name: "twitter:description",
          content: this.article.description,
        },

        {
          hid: "twitter:image",
          name: "twitter:image",
          content: this.ogImageUrl,
        },
      ],
    };
  },

  computed: {
    ogImageUrl() {
      return this.$cloudinary.image.url(
        "automatic-social-share-images-nuxtjs/template/og-template",
        {
          transformation: [
            {
              overlay:
                "automatic-social-share-images-nuxtjs:photo-1494253109108-2e30c049369b",
              gravity: "north",
              height: "400",
              width: "700",
            },
            {
              overlay: "automatic-social-share-images-nuxtjs:avataaars",
              gravity: "south_west",
              height: "50",
              width: "50",
              x: "250",
              y: "100",
            },
            {
              overlay: {
                font_family: "Arial",
                font_size: 24,
                font_weight: "bold",
                text: this.article.title,
              },
              gravity: "south_west",
              co_rgb: "000000",
              x: "250",
              y: "175",
            },
            {
              overlay: {
                font_family: "Arial",
                font_size: 18,
                font_weight: "normal",
                text: this.article.author,
              },
              gravity: "south_west",
              co_rgb: "000000",
              x: "325",
              y: "115",
            },
          ],
        }
      );
    },
  },
};
</script>