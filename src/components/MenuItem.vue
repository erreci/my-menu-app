<template>
    <li>
      <router-link :to="to" class="block py-2 px-4 hover:bg-gray-700 rounded">
        {{ text }}
      </router-link>
    </li>
  </template>
  
  <script setup lang="ts">
  defineProps<{
    to: string;
    text: string;
  }>();
  </script>