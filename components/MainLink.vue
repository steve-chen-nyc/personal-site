<template>
  <nuxt-link :to="`/${title}`">
    <div class="bg-blue-500 flex items-center justify-center mt-4 h-12">
      <h5 class="text-center uppercase">{{ title }}</h5>
    </div>
  </nuxt-link>
</template>

<script>
export default {
  props: {
    title: {
      type: String,
      required: true,
    },
  },
}
</script>
