<template>
  <section
    class="bg-white h-48 flex items-center justify-between px-8 w-3/5 c-main__animate"
  >
    <div class="w-1/2">
      <h1 class="text-black uppercase">Steve Chen</h1>
      <h5>Software Engineer</h5>
    </div>
    <div class="w-48 transform rotate-90">
      <MainLink v-for="link in links" :title="link" :key="link" />
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      links: ['blog', 'timeline', 'skills'],
    }
  },
}
</script>
