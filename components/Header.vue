<template>
  <nav class="flex items-center justify-between flex-wrap bg-gray-500 p-6">
    <div class="flex items-center flex-shrink-0 text-white mr-6">
      <nuxt-link to="/">
        <span class="font-semibold text-xl tracking-tight uppercase"
          >Steve's site</span
        >
      </nuxt-link>
    </div>
    <div class="w-full block flex-grow lg:flex lg:items-center lg:w-auto">
      <div class="text-sm lg:flex-grow">
        <nuxt-link
          to="/tech"
          class="block mt-4 lg:inline-block lg:mt-0 text-teal-200 hover:text-white mr-4"
        >
          Code
        </nuxt-link>
      </div>
    </div>
  </nav>
</template>
