<script setup lang="ts">
import RecentOrderTable from '../tables/RecentOrderTable.vue'
</script>

<template>
  <div class="space-y-6">
    <!-- Título y Breadcrumb -->
    <div>
      <h1 class="text-2xl font-semibold text-gray-800">Recent Orders</h1>
      <nav class="text-sm text-gray-500 mt-1">
        <ol class="flex items-center space-x-2">
          <li>
            <a href="#" class="hover:underline text-blue-600">Home</a>
          </li>
          <li>/</li>
          <li class="text-gray-700">Recent Orders</li>
        </ol>
      </nav>
    </div>

    <!-- Tabla de órdenes -->
    <RecentOrderTable />
  </div>
</template>