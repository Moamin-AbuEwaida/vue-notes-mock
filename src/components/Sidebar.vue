<template>
  <aside class="w-[256px] min-h-screen bg-gray-800">
    <div class="p-4">
      <button class="button w-full">New Note</button>
    </div>
    <ul>
      <li
        class="p-4 border-b border-gray-700 hover:bg-gray-600 cursor-pointer flex justify-between items-center gap-4"
      >
        <span>Note Title</span>
        <i
          class="pi pi-times text-red-600 transition-transform duration-50 hover:rotate-30"
        ></i>
      </li>
    </ul>
  </aside>
</template>

<script>
export default {};
</script>

<style></style>
