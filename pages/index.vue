<template>
  <div class="xl:max-w-screen-xl">
    <div class="mt-20 mx-auto">
      <img
        class="rounded-full mx-auto"
        :src="avatar + '?fit=scale&w=350&h=350'"
        :srcset="`${avatar}?w=350&h=350&fit=fill 350w, ${avatar}?w=700&h=700&fit=fill 1000w, ${avatar}?w=1050&h=1050&fit=fill 2000w`"
        sizes="(min-width: 1024px) 400px, 100vw"
      />
      <h1 class="text-center mt-10">{{ bio }}</h1>
    </div>
  </div>
</template>

<script>
import { createClient } from '~/plugins/contentful.js'

const client = createClient()

export default {
  // `env` is available in the context object
  asyncData({ env }) {
    return Promise.all([
      client.getEntries({
        content_type: env.CTF_ME_ID,
      }),
    ])
      .then(([entries]) => {
        const meData = entries.items[0].fields

        return {
          bio: meData.bio,
          avatar: meData.avatar.fields.file.url,
          host: 'https',
        }
      })
      .catch(console.error)
  },
}
</script>
