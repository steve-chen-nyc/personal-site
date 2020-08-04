<template>
  <div
    class="xl:max-w-screen-xl mx-auto justify-center flex items-center flex-col"
  >
    <div class="mt-20">
      <img
        class="rounded-full"
        :src="avatar + '?fit=scale&w=350&h=350'"
        :srcset="`${avatar}?w=350&h=350&fit=fill 350w, ${avatar}?w=700&h=700&fit=fill 1000w, ${avatar}?w=1050&h=1050&fit=fill 2000w`"
        sizes="(min-width: 1024px) 400px, 100vw"
      />
      <h1 class="text-center mt-10">{{ bio }}</h1>
    </div>

    <div class="mt-20 flex flex-wrap justify-center lg:flex-no-wrap">
      <div
        v-for="media in interestsMedia"
        class="mb-20 lg:mb-0 lg:mr-20 last:mr-0"
      >
        <img
          :src="`${media.fields.file.url}?fit=scale&w=300&h=300`"
          :srcset="`${media.fields.file.url}?w=350&h=350&fit=fill 350w, ${media.fields.file.url}?w=700&h=700&fit=fill 1000w, ${media.fields.file.url}?w=1050&h=1050&fit=fill 2000w`"
          sizes="(min-width: 1024px) 700px, 100vw"
        />
        <p>{{ media.fields.title }}</p>
      </div>
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
          interestsMedia: meData.interests_media,
        }
      })
      .catch(console.error)
  },
}
</script>
