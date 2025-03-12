<script setup>
import { ref } from "vue";
import Sidebar from "./components/Sidebar.vue";

const notes = ref([]);
const activeNote = ref(null);
const inputTitle = ref("");
const noteContent = ref("");

// create note
const createNote = () => {
  // random id
  const id = Math.random().toString(36).substring(2, 9);
  notes.value.push({
    id,
    title: "untitled",
    content: "",
  });
  setActiveNote(id);
};
// set Active note
const setActiveNote = (id) => {
  activeNote.value = id;
  let note = notes.value.find((note) => note.id === id);

  inputTitle.value = note.title;
  noteContent.value = note.content;

  setTimeout(() => {
    document.querySelector('input[type="text"]').focus();
  }, 0);
};
// delete note
const deleteNote = ({ id, e }) => {
  e.stopPropagation();
  let note = notes.value.findIndex((note) => note.id === id);
  notes.value.splice(note, 1);

  activeNote.value = null;
  inputTitle.value = "";
  noteContent.value = "";
};
// update note
const updateNote = () => {
  let note = notes.value.findIndex((note) => note.id === activeNote.value);
  notes.value[note].title = inputTitle.value;
  notes.value[note].content = noteContent.value;
};
</script>

<template>
  <div
    class="bg-gray-700 text-white min-h-screen flex items-stretch justify-start"
  >
    <!-- sidebar -->
    <Sidebar
      :activeNote="activeNote"
      :notes="notes"
      @newNote="createNote"
      @setActiveNote="setActiveNote"
      @deleteNote="deleteNote"
    />
    <!-- main content -->
    <main class="flex-1">
      <div v-if="activeNote" class="px-4 py-8 flex flex-col h-full">
        <input
          v-model="inputTitle"
          @input="updateNote"
          type="text"
          class="block w-full text-3xl pb-2 font-bold border-b-2 border-gray-500 focus:border-white outline-none transition-colors duration-200"
        />
        <textarea
          v-model="noteContent"
          @input="updateNote"
          class="block w-full h-full mt-4 text-lg outline-none flex-1"
        ></textarea>
      </div>
    </main>
  </div>
</template>
