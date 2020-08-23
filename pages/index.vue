<script>
export default {
  data: () => ({
    animate: false,
  }),
  mounted() {
    setTimeout(() => {
      this.animate = true
    }, 3000)
  },
}
</script>

<template>
  <div class="bg-black w-screen h-screen flex w-full items-center">
    <Main v-if="animate"></Main>
  </div>
</template>
