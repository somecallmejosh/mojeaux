<template>
  <div>
    <div class="shadow-lg px-6">
      <div class="container mx-auto h-20 flex justify-between items-center">
        <div class="text-2xl font-bold">
          möjëäüx
        </div>
        <nav class="flex h-full items-center">
          <a
            href="#mission"
            class="flex h-full items-center text-blue-600 hover:underline"
            >Mission</a
          >
          <a
            href="#portfolio"
            class="flex h-full items-center text-blue-600 hover:underline mx-12"
            >Portfolio</a
          >
          <a
            href="#contact"
            class="flex h-full items-center text-blue-600 hover:underline"
            >Contact Us</a
          >
        </nav>
      </div>
    </div>
    <Nuxt />
  </div>
</template>

<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
  scroll-behavior: smooth;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}
</style>
