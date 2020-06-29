<template>
  <div :class="menuIsActive ? 'fixed' : ''">
    <div
      class="offsite lg:hidden h-screen w-2/3 fixed top-0 left-0 bg-white shadow-lg z-30"
      :class="menuIsActive ? 'active' : ''"
    >
      <nav class="my-4 block w-full" @click="toggleMenu">
        <a
          href="#mission"
          class="block text-blue-600 p-6 border-b border-gray-400"
          >Mission</a
        >
        <a
          href="#portfolio"
          class="block text-blue-600 p-6 border-b border-gray-400"
          >Portfolio</a
        >
        <a
          href="#contact"
          class="block text-blue-600 p-6 border-b border-gray-400"
          >Contact Us</a
        >
      </nav>
      <div class="flex p-2">
        <button
          class="bg-blue-500 text-white px-4 py-1 rounded ml-auto font-bold"
          @click="toggleMenu"
        >
          Close Menu
        </button>
      </div>
    </div>
    <div
      v-if="menuIsActive"
      class="fixed z-10 w-screen h-screen bg-black bg-opacity-75"
      @click="toggleMenu"
    ></div>
    <div class="relative z-0">
      <div class="shadow-lg px-6">
        <div class="container mx-auto h-20 flex justify-between items-center">
          <div class="flex items-center font-semibold">
            <div
              class="bg-blue-400 mr-1 h-12 w-12 rounded-full flex items-center justify-center text-white"
            >
              <logo class="h-8 fill-current mt-1 mr-px" />
            </div>
            <span>moejoe web services</span>
          </div>
          <div class="lg:hidden">
            <button
              class="menu-toggle p-0 flex items-center text-gray-800 hover:text-blue-700"
              @click="toggleMenu"
            >
              <div class="w-6" aria-hidden>
                <span></span>
                <span></span>
                <span></span>
              </div>
            </button>
          </div>
          <nav class="hidden lg:flex lg:h-full lg:items-center">
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
  </div>
</template>
<script>
import Logo from '~/components/svg/logo'
export default {
  components: { Logo },
  data() {
    return {
      menuIsActive: false,
    }
  },
  methods: {
    toggleMenu() {
      this.menuIsActive = !this.menuIsActive
    },
  },
}
</script>
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

.menu-toggle span {
  display: block;
  background: currentColor;
  height: 4px;
  width: 100%;
  margin-bottom: 2px;
}

.offsite {
  transition: all 0.2s;
  transform: translateX(-100%);
  z-index: 100 !important;
}
.offsite.active {
  transform: translateX(0);
}
</style>
