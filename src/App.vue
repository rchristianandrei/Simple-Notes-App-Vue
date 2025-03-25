<script setup lang="ts">
import { ref } from "vue";
import Card from "./components/Card.vue"
import AddNote from "./components/AddNote.vue"

const notes = ref<{
  title: string,
  content: string,
  date: Date
}[]>([
  {title: "My Addresssss", content: "Sample content", date: new Date},
  {title: "My Codes", content: "Sample content", date: new Date},
  {title: "Watch List", content: "Sample content", date: new Date},
  ])

const addNoteDialog = ref(false)

function AddNoteCb(note: {title: string, content: string, date: Date}){
  notes.value.push(note)
}
</script>

<template>
  <div class="max-w-[1000px] mx-auto">
    <header class="flex items-center justify-between px-3 py-5">
      <h1 class="text-3xl font-semi">Notes App</h1>
      <button @click="addNoteDialog = !addNoteDialog" class="cursor-pointer border bg-white w-13 h-13 rounded-full hover:opacity-[.75]"><span class="pi pi-plus"></span></button>
    </header>
    <main class="p-3 flex gap-1 flex-wrap">
      <Card v-for="(note, index) in notes" :key="index" :title="note.title" :content="note.content" :date="note.date"></Card>
    </main>
  </div>

  <AddNote v-if="addNoteDialog" @add="AddNoteCb" @close="addNoteDialog = false"></AddNote>
</template>

<style scoped>

</style>
