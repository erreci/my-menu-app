<template>
  <div class="flex h-screen">
    <button @click="toggleMenu" class="lg:hidden fixed top-4 left-4 z-50 p-2 text-white bg-gray-800">
      <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
      </svg>
    </button>
    <aside v-show="isMobile ? menuOpen : true" class="fixed inset-y-0 left-0 w-64 bg-gray-800 text-white p-4 z-40 transition-transform duration-300 ease-in-out"
           :style="{transform: isMobile && !menuOpen ? 'translateX(-100%)' : 'translateX(0)'}">
      <ul>
        <MenuItem to="/" text="Home" />
        <MenuItem to="/about" text="About" />
        <MenuItem to="/contact" text="Contact" />
      </ul>
    </aside>
    <main class="flex-1 p-4">
      <router-view />
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref, computed, watch } from 'vue';
import MenuItem from './MenuItem.vue';

const menuOpen = ref(false);
const toggleMenu = () => (menuOpen.value = !menuOpen.value);
const isMobile = computed(() => window.innerWidth < 768);

watch(isMobile, (newIsMobile) => {
  if (newIsMobile && menuOpen.value) {
    menuOpen.value = false; // Close menu if screen size changes to mobile
  }
});

</script>