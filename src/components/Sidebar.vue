<script setup>
const props = defineProps(["activeNote", "notes"]);
</script>

<template>
  <aside class="w-[256px] min-h-screen bg-gray-800">
    <div class="p-4">
      <button class="button w-full" @click="$emit('newNote')">New Note</button>
    </div>
    <ul>
      <li
        v-for="note in props.notes"
        :key="note.id"
        @click="$emit('setActiveNote', note.id)"
        class="p-4 border-b border-gray-700 hover:bg-gray-600 cursor-pointer flex justify-between items-center gap-4"
      >
        <span>{{ note.title }}</span>
        <i
          @click="(e) => $emit('deleteNote', { id: note.id, e })"
          class="pi pi-times text-red-600 transition-transform duration-50 hover:rotate-30"
        ></i>
      </li>
    </ul>
  </aside>
</template>
