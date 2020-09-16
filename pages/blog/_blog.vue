<template>
  <div>
    <div class="pt-20 pl-20">
      <div class="flex justify-end mr-10">
        <nuxt-link to="/blog">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            class="h-8 w-8 mr-5 stroke-current text-white hover:text-blue-500"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M7 16l-4-4m0 0l4-4m-4 4h18"
            />
          </svg>
        </nuxt-link>
        <nuxt-link to="/">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            class="h-8 w-8 stroke-current text-white hover:text-blue-500"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"
            />
          </svg>
        </nuxt-link>
      </div>
    </div>
    <div class="w-full p-20">
      <article
        class="tech-article text-white"
        v-html="$md.render(post.fields.body)"
      ></article>
    </div>
  </div>
</template>
<script>
import { createClient } from '~/plugins/contentful.js'

const client = createClient()

export default {
  asyncData({ env, params }) {
    const { tech: slug } = params
    return Promise.all([
      client.getEntries({
        content_type: env.CTF_BLOG_POST_TYPE_ID,
        'fields.slug': slug,
      }),
    ])
      .then(([posts]) => {
        return {
          post: posts.items[0],
        }
      })
      .catch(console.error)
  },
}
</script>

<style lang="sass">
article
  h1, h2, h3, p, ul
    margin-bottom: 2rem
</style>
