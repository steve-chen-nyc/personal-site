<template>
  <section
    class="bg-white h-48 flex flex-col lg:flex-row items-center justify-between px-8 w-full lg:w-3/5"
  >
    <div class="mt-4 text-center lg:text-left lg:m-0 lg:w-1/2">
      <h1 class="uppercase">Steve Chen</h1>
      <h5>Software Engineer</h5>
      <div class="flex justify-center lg:justify-start items-center mt-4">
        <a
          class="w-8 mr-4"
          href="https://www.linkedin.com/in/stevechen4/"
          target="_blank"
        >
          <img src="~/assets/linkedin.png" />
        </a>
        <a class="w-8" href="https://github.com/steve-chen-nyc" target="_blank">
          <img class="w-8" src="~/assets/github.png" />
        </a>
      </div>
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
