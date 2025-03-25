<script setup lang="ts">
import { reactive } from 'vue';

const emit = defineEmits<{
    (event: "add", value: {title: string, content: string, date: Date}): void
    (event: "close"): void
}>()

const note = reactive({title: "", content:""})

function addNote(){
    emit("add", {title: note.title, content: note.content, date: new Date})
    emit("close")
}
</script>

<template>
    <div role="dialog" 
  class="fixed inset-[0] bg-gray-400 opacity-[.5]">
    </div>
    <div class="fixed inset-[0] flex justify-center items-center">
        <form @submit.prevent="addNote" class="bg-white p-5 rounded shadow-lg">
            <div class="flex justify-between mb-3">
                <h1 class="text-xl">Add Note</h1>
                <button @click="emit('close')" type="button" class="cursor-pointer pi pi-times"></button>
            </div>
            <div class="flex flex-col my-2">
                <label for="">Title</label>
                <input v-model.trim="note.title" type="text" placeholder="Title.." class="border rounded p-2">
            </div>
            <div class="flex flex-col my-2">
                <label for="">Content</label>
                <input v-model.trim="note.content" type="text" placeholder="Content.." class="border rounded p-2">
            </div>
            <button type="submit" class="cursor-pointer bg-blue-300 w-[100%] rounded p-2 font-semibold">Add</button>
        </form>
    </div>
</template>