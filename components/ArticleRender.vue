<template>
  <div class="relative py-16 bg-white overflow-hidden">
    <div class="hidden lg:block lg:absolute lg:inset-y-0 lg:h-full lg:w-full">
      <div
        class="relative h-full text-lg max-w-prose mx-auto"
        aria-hidden="true"
      >
        <svg
          class="absolute top-12 left-full transform translate-x-32"
          width="404"
          height="384"
          fill="none"
          viewBox="0 0 404 384"
        >
          <defs>
            <pattern
              id="74b3fd99-0a6f-4271-bef2-e80eeafdf357"
              x="0"
              y="0"
              width="20"
              height="20"
              patternUnits="userSpaceOnUse"
            >
              <rect
                x="0"
                y="0"
                width="4"
                height="4"
                class="text-gray-200"
                fill="currentColor"
              />
            </pattern>
          </defs>
          <rect
            width="404"
            height="384"
            fill="url(#74b3fd99-0a6f-4271-bef2-e80eeafdf357)"
          />
        </svg>
        <svg
          class="
            absolute
            top-1/2
            right-full
            transform
            -translate-y-1/2 -translate-x-32
          "
          width="404"
          height="384"
          fill="none"
          viewBox="0 0 404 384"
        >
          <defs>
            <pattern
              id="f210dbf6-a58d-4871-961e-36d5016a0f49"
              x="0"
              y="0"
              width="20"
              height="20"
              patternUnits="userSpaceOnUse"
            >
              <rect
                x="0"
                y="0"
                width="4"
                height="4"
                class="text-gray-200"
                fill="currentColor"
              />
            </pattern>
          </defs>
          <rect
            width="404"
            height="384"
            fill="url(#f210dbf6-a58d-4871-961e-36d5016a0f49)"
          />
        </svg>
        <svg
          class="absolute bottom-12 left-full transform translate-x-32"
          width="404"
          height="384"
          fill="none"
          viewBox="0 0 404 384"
        >
          <defs>
            <pattern
              id="d3eb07ae-5182-43e6-857d-35c643af9034"
              x="0"
              y="0"
              width="20"
              height="20"
              patternUnits="userSpaceOnUse"
            >
              <rect
                x="0"
                y="0"
                width="4"
                height="4"
                class="text-gray-200"
                fill="currentColor"
              />
            </pattern>
          </defs>
          <rect
            width="404"
            height="384"
            fill="url(#d3eb07ae-5182-43e6-857d-35c643af9034)"
          />
        </svg>
      </div>
    </div>
    <div class="relative px-4 sm:px-6 lg:px-8">
      <div class="text-lg max-w-prose mx-auto">
        <h1>
          <span
            class="
              mt-2
              block
              text-3xl text-center
              leading-8
              font-extrabold
              tracking-tight
              text-gray-900
              sm:text-4xl
            "
            >{{ article.title }}</span
          >
        </h1>
        <img class="my-10" :src="$cloudinary.image.url(article.image)" />
      </div>
      <div class="prose prose-indigo prose-lg text-gray-500 mx-auto">
        <div class="flex flex-row-reverse">
          <div class="flex items-center">
            <div>
              <img
                class="inline-block h-9 w-9 rounded-full mr-2"
                style="margin: 0"
                :src="$cloudinary.image.url(article.author_avatar)"
                alt=""
              />
            </div>
            <div class="ml-3">
              <p
                class="
                  text-sm
                  font-medium
                  text-gray-700
                  group-hover:text-gray-900
                "
              >
                {{ article.author }}
              </p>
            </div>
          </div>
        </div>
        <nuxt-content :document="article" />
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    article: {
      required: true,
      type: Object,
    },
  },
};
</script>