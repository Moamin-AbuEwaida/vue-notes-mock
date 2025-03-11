<script setup>
import Sidebar from "./components/Sidebar.vue";
</script>

<template>
  <div
    class="bg-gray-700 text-white min-h-screen flex items-stretch justify-start"
  >
    <!-- sidebar -->
    <Sidebar />
    <!-- main content -->
    <main class="flex-1">
      <div class="px-4 py-8 flex flex-col h-full">
        <input
          type="text"
          class="block w-full text-3xl pb-2 font-bold border-b-2 border-gray-500 focus:border-white outline-none transition-colors duration-200"
        />
      </div>
    </main>
  </div>
</template>
