<template>
  <section
    class="bg-white h-48 flex items-center justify-between px-8 w-3/5 c-main__animate"
  >
    <div class="w-1/2">
      <h1 class="text-black">Steve Chen</h1>
      <h5>Software Engineer</h5>
    </div>
    <div class="w-48 transform rotate-90">
      <div class="bg-blue-500 flex items-center justify-center mt-4 h-12">
        <h5 class="text-center uppercase">Timeline</h5>
      </div>
      <div class="bg-blue-500 flex items-center justify-center mt-8 h-12">
        <h5 class="text-center uppercase">Skills</h5>
      </div>
      <div class="bg-blue-500 flex items-center justify-center mt-8 h-12">
        <h5 class="text-center uppercase">Articles</h5>
      </div>
    </div>
  </section>
</template>

<style>
@keyframes slideInFromLeft {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(0);
  }
}

.c-main__animate {
  animation: 1s ease-in slideInFromLeft;
}
</style>
