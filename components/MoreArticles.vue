<template>
  <div
    class="
      relative
      bg-gray-50
      pt-16
      pb-20
      px-4
      sm:px-6
      lg:pt-24 lg:pb-28 lg:px-8
    "
  >
    <div class="absolute inset-0">
      <div class="bg-white h-1/3 sm:h-2/3" />
    </div>
    <div class="relative max-w-7xl mx-auto">
      <div class="text-center">
        <h2
          class="
            text-3xl
            tracking-tight
            font-extrabold
            text-gray-900
            sm:text-4xl
          "
        >
          More articles
        </h2>
      </div>
      <div
        class="mt-12 max-w-lg mx-auto grid gap-5 lg:grid-cols-3 lg:max-w-none"
      >
        <div
          v-for="(article, key) in articles"
          :key="key"
          class="flex flex-col rounded-lg shadow-lg overflow-hidden"
        >
          <div class="flex-shrink-0">
            <img
              class="h-48 w-full object-cover"
              :src="$cloudinary.image.url(article.image)"
              alt=""
            />
          </div>
          <div class="flex-1 bg-white p-6 flex flex-col justify-between">
            <div class="flex-1">
              <nuxt-link :to="article.path" class="block mt-2">
                <p class="text-xl font-semibold text-gray-900">
                  {{ article.title }}
                </p>
                <p class="mt-3 text-base text-gray-500">
                  {{ article.description }}
                </p>
              </nuxt-link>
            </div>
            <div class="mt-6 flex items-center">
              <div class="flex-shrink-0">
                <nuxt-link :to="article.path">
                  <span class="sr-only">{{ article.author }}</span>
                  <img
                    class="h-10 w-10 rounded-full"
                    :src="$cloudinary.image.url(article.author_avatar)"
                    alt=""
                  />
                </nuxt-link>
              </div>
              <div class="ml-3">
                <p class="text-sm font-medium text-gray-900">
                  <nuxt-link :to="article.path" class="hover:underline">
                    {{ article.author }}
                  </nuxt-link>
                </p>
                <div class="flex space-x-1 text-sm text-gray-500">
                  <time :datetime="article.createdAt">
                    {{ article.createdAt }}
                  </time>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    articles: {
      required: true,
      type: Array,
    },
  },
};
</script>