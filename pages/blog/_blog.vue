<template>
  <article class="tech-article" v-html="$md.render(post.fields.body)"></article>
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
