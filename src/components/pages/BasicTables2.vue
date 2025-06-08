<template>
  <div class="space-y-6">
    <!-- Breadcrumb y título -->
    <div class="flex items-center justify-between">
      <div>
        <h1 class="text-2xl font-semibold text-gray-800">Basic Tables</h1>
        <nav class="text-sm text-gray-500 mt-1">
          <ol class="flex space-x-2">
            <li><a href="#" class="hover:underline">Home</a></li>
            <li>/</li>
            <li class="text-gray-700">Basic Tables</li>
          </ol>
        </nav>
      </div>
    </div>

    <!-- Tabla 1 -->
    <div class="bg-white p-6 rounded-lg shadow">
      <h2 class="text-lg font-semibold mb-4">Basic Table 1</h2>
      <table class="w-full text-sm text-left border-separate border-spacing-y-2">
        <thead>
          <tr class="text-gray-500">
            <th>User</th>
            <th>Project Name</th>
            <th>Team</th>
            <th>Status</th>
            <th>Budget</th>
          </tr>
        </thead>
        <tbody>
          <tr
            v-for="user in users"
            :key="user.name"
            class="bg-gray-50 hover:bg-gray-100 rounded"
          >
            <td class="py-2 flex items-center gap-2">
              <img :src="user.avatar" class="w-8 h-8 rounded-full" />
              <div>
                <p class="font-medium text-gray-700">{{ user.name }}</p>
                <p class="text-xs text-gray-500">{{ user.role }}</p>
              </div>
            </td>
            <td>{{ user.project }}</td>
            <td>
              <div class="flex -space-x-1">
                <img v-for="n in user.teamCount" :key="n" class="w-6 h-6 rounded-full border-2 border-white" src="https://randomuser.me/api/portraits/lego/1.jpg" />
              </div>
            </td>
            <td>
              <span
                :class="[
                  'px-2 py-1 rounded text-xs font-medium',
                  user.status === 'Active' ? 'bg-green-100 text-green-700' :
                  user.status === 'Pending' ? 'bg-yellow-100 text-yellow-700' :
                  'bg-red-100 text-red-700'
                ]"
              >
                {{ user.status }}
              </span>
            </td>
            <td>{{ user.budget }}</td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<script setup lang="ts">
const users = [
  {
    name: 'Lindsey Curtis',
    role: 'Web Designer',
    project: 'Agency Website',
    status: 'Active',
    budget: '3.9K',
    teamCount: 4,
    avatar: 'https://randomuser.me/api/portraits/women/44.jpg',
  },
  {
    name: 'Kaiya George',
    role: 'Project Manager',
    project: 'Technology',
    status: 'Pending',
    budget: '24.9K',
    teamCount: 2,
    avatar: 'https://randomuser.me/api/portraits/women/68.jpg',
  },
  {
    name: 'Zain Geidt',
    role: 'Content Writer',
    project: 'Blog Writing',
    status: 'Active',
    budget: '12.7K',
    teamCount: 1,
    avatar: 'https://randomuser.me/api/portraits/men/22.jpg',
  },
  {
    name: 'Abram Schleifer',
    role: 'Digital Marketer',
    project: 'Social Media',
    status: 'Cancel',
    budget: '2.8K',
    teamCount: 3,
    avatar: 'https://randomuser.me/api/portraits/men/1.jpg',
  },
]
</script>

<style lang="scss" scoped>

</style>