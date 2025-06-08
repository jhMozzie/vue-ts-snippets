<template>
  <div class="flex min-h-screen">
    <Sidebar />
    <div class="flex-1 overflow-y-auto p-6 bg-gray-100">
      <slot />
    </div>
  </div>
</template>

<script setup lang="ts">
import Sidebar from './Sidebar.vue'
</script>