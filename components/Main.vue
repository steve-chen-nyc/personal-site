<template>
  <section
    class="bg-white h-48 flex flex-col lg:flex-row items-center justify-between px-8 w-full lg:w-3/5 c-main__animate"
  >
    <div class="mt-4 lg:m-0 lg:w-1/2">
      <h1 class="text-center uppercase">Steve Chen</h1>
      <h5>Software Engineer</h5>
    </div>
    <div class="w-full w-full lg:w-48 transform lg:rotate-90">
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
