<template>
  <Nuxt />
</template>

<style>
@tailwind base;

html {
  font-family: 'Open Sans Condensed', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

body {
  background-color: #000;
  height: 100%;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

h1 {
  font-weight: 300;
  @apply text-4xl;
}
h2 {
  @apply text-3xl;
}
h3 {
  @apply text-2xl;
}

h4 {
  @apply text-xl;
}

h5 {
  @apply text-lg;
}

.roboto {
  font-family: 'Roboto', sans-serif;
}

@tailwind components;
@tailwind utilities;
</style>
