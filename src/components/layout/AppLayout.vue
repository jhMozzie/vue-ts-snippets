<template>
  <div class="flex min-h-screen bg-gray-100">
    <!-- Sidebar a la izquierda -->
    <Sidebar2 />

    <!-- Contenido a la derecha -->
    <div class="flex-1 overflow-y-auto p-6">
      <slot />
    </div>
  </div>
</template>

<script setup lang="ts">
import Sidebar2 from './Sidebar2.vue'
</script>