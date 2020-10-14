<template>
  <client-only>
    <div>
      <nuxt-link to="/">
        <div class="flex justify-end mr-10 mt-20">
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
        </div>
      </nuxt-link>

      <vue-pdf
        class="pdf-viewer mx-40 my-10"
        :src="pdfSrc"
        :page="1"
        @num-pages="pdfPageCount = $event"
      ></vue-pdf>
    </div>
  </client-only>
</template>

<script>
export default {
  data() {
    return { pdfSrc: 'Steve_Chen_Resume_v7.pdf', pdfPageCount: 0 }
  },
}
</script>
