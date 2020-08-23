<template>
  <div>
    <ul>
      <li v-for="post in posts">
        <nuxt-link :to="'/tech/' + post.fields.slug">
          {{ post.fields.title }}
        </nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
import { createClient } from '~/plugins/contentful.js'

const client = createClient()

export default {
  asyncData({ env, params }) {
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
