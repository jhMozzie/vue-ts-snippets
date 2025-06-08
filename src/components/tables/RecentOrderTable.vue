<template>
  <div class="bg-white p-6 rounded-lg shadow space-y-4">
    <div class="flex items-center justify-between">
      <h2 class="text-lg font-semibold">Recent Orders</h2>
      <div class="flex items-center gap-2">
        <input
          v-model="search"
          type="text"
          placeholder="Search..."
          class="px-3 py-2 border rounded-lg text-sm focus:outline-none focus:ring-2 focus:ring-blue-500"
        />
        <button class="inline-flex items-center gap-1 px-4 py-2 border rounded-lg text-sm font-medium hover:bg-gray-100">
          <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2"
            viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round"
              d="M3 4a1 1 0 011-1h16a1 1 0 011 1v2a1 1 0 01-.293.707L15 14.414V19a1 1 0 01-.553.894l-4 2A1 1 0 019 21v-6.586L3.293 6.707A1 1 0 013 6V4z" />
          </svg>
          Filter
        </button>
      </div>
    </div>

    <table class="w-full text-sm text-left border-separate border-spacing-y-2">
      <thead class="bg-gray-50 text-gray-600">
        <tr class="text-gray-500">
          <th class="px-4 py-3"><input type="checkbox" /></th>
          <th class="px-4 py-3">Deal ID</th>
          <th class="px-4 py-3">Customer</th>
          <th class="px-4 py-3">Product/Service</th>
          <th class="px-4 py-3">Deal Value</th>
          <th class="px-4 py-3">Close Date</th>
          <th class="px-4 py-3">Status</th>
          <th class="px-4 py-3">Action</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="order in filteredOrders"
          :key="order.id"
          class="bg-gray-50 hover:bg-gray-100 rounded"
        >
          <td class="px-4 py-3"><input type="checkbox" /></td>
          <td class="px-4 py-3">{{ order.id }}</td>
          <td class="flex items-center gap-2 py-2">
            <div class="w-8 h-8 rounded-full flex items-center justify-center font-bold text-white" :style="{ backgroundColor: order.color }">
              {{ order.initials }}
            </div>
            <div>
              <p class="font-medium text-gray-700">{{ order.name }}</p>
              <p class="text-xs text-gray-500">{{ order.email }}</p>
            </div>
          </td>
          <td class="px-4 py-3">{{ order.product }}</td>
          <td class="px-4 py-3">{{ order.value }}</td>
          <td class="px-4 py-3">{{ order.date }}</td>
          <td class="px-4 py-3">
            <span
              :class="[
                'px-2 py-1 rounded text-xs font-medium',
                order.status === 'Complete' ? 'bg-green-100 text-green-700' :
                order.status === 'Pending' ? 'bg-yellow-100 text-yellow-700' :
                'bg-red-100 text-red-700'
              ]"
            >
              {{ order.status }}
            </span>
          </td>
          <td class="px-4 py-3">
            <button class="text-red-600 hover:text-red-800">
              <svg xmlns="http://www.w3.org/2000/svg" class="w-5 h-5" fill="none"
                viewBox="0 0 24 24" stroke="currentColor" stroke-width="2">
                <path stroke-linecap="round" stroke-linejoin="round"
                  d="M6 18L18 6M6 6l12 12" />
              </svg>
            </button>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'

const search = ref('')

const orders = ref([
  {
    id: 'DE124321',
    initials: 'JD',
    name: 'John Doe',
    email: 'johndoe@gmail.com',
    product: 'Software License',
    value: '$18,50.34',
    date: '2024-06-15',
    status: 'Complete',
    color: '#7C3AED',
  },
  {
    id: 'DE124322',
    initials: 'KF',
    name: 'Kierra Franci',
    email: 'kierra@gmail.com',
    product: 'Software License',
    value: '$18,50.34',
    date: '2024-06-15',
    status: 'Complete',
    color: '#EC4899',
  },
  {
    id: 'DE124323',
    initials: 'EW',
    name: 'Emerson Workman',
    email: 'emerson@gmail.com',
    product: 'Software License',
    value: '$18,50.34',
    date: '2024-06-15',
    status: 'Pending',
    color: '#38BDF8',
  },
  {
    id: 'DE124324',
    initials: 'CP',
    name: 'Chance Philips',
    email: 'chance@gmail.com',
    product: 'Software License',
    value: '$18,50.34',
    date: '2024-06-15',
    status: 'Complete',
    color: '#F59E0B',
  },
  {
    id: 'DE124325',
    initials: 'TG',
    name: 'Terry Geidt',
    email: 'terry@gmail.com',
    product: 'Software License',
    value: '$18,50.34',
    date: '2024-06-15',
    status: 'Complete',
    color: '#10B981',
  },
])

const filteredOrders = computed(() => {
  return orders.value.filter(order =>
    order.name.toLowerCase().includes(search.value.toLowerCase()) ||
    order.email.toLowerCase().includes(search.value.toLowerCase())
  )
})
</script>