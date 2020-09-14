<template>
  <div class="w-full">
    <div class="pt-20 pl-20">
      <nuxt-link to="/">
        <div class="flex justify-end mr-10">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            fill="none"
            viewBox="0 0 24 24"
            stroke="#fff"
            class="h-8 w-8"
          >
            <path
              stroke-linecap="round"
              stroke-linejoin="round"
              stroke-width="2"
              d="M3 12l2-2m0 0l7-7 7 7M5 10v10a1 1 0 001 1h3m10-11l2 2m-2-2v10a1 1 0 01-1 1h-3m-6 0a1 1 0 001-1v-4a1 1 0 011-1h2a1 1 0 011 1v4a1 1 0 001 1m-6 0h6"
            />
          </svg>
        </div>
      </nuxt-link>
      <h1 class="text-white mb-5">KNOWLEDGE</h1>
      <ul>
        <li class="text-white uppercase" v-for="post in posts">
          <nuxt-link :to="`/blog/${post.fields.slug}`">
            {{ post.fields.title }}
            <span class="pl-5">{{ post.fields.description }}</span>
            <span class="pl-5 italic"
              >Published:
              {{
                $dateFns.format(
                  new Date(post.fields.publishDate),
                  'MM-dd-yyyy hh:mm a'
                )
              }}
            </span>
          </nuxt-link>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import { createClient } from '~/plugins/contentful.js'

const client = createClient()

export default {
  asyncData({ env, params, $dateFns }) {
    return Promise.all([
      client.getEntries({
        content_type: env.CTF_BLOG_POST_TYPE_ID,
        order: '-sys.createdAt',
      }),
    ])
      .then(([posts]) => {
        return {
          posts: posts.items,
        }
      })
      .catch(console.error)
  },
}
</script>
