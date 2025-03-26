<script setup lang="ts">
defineProps<{
  id: number,
  title: string,
  content: string,
  date: Date
}>()

const emit = defineEmits<{
  (event: "edit", value: number): void,
  (event: "delete", value: number): void,
}>()

</script>

<template>
    <div class="bg-blue-300 w-50 rounded p-3">
      <div class="h-[30px] flex justify-between items-center">
        <h2 class="text-lg font-bold overflow-clip">{{ title }}</h2>
        <div class="group pi pi-ellipsis-v cursor-pointer rounded-full p-1 relative">
          <ul class="absolute right-0 bg-white text-black p-1 flex flex-col gap-2 rounded hidden group-hover:block">
            <li @click="emit('edit', id)" class="cursor-pointer hover:opacity-[.5]">Edit</li>
            <li @click="emit('delete', id)" class="cursor-pointer hover:opacity-[.5]">Delete</li>
          </ul>
        </div>
      </div>
      <div class="overflow-clip h-[200px]">{{content}}</div>
      <div class="italic text-right">{{date.toLocaleDateString("en-US")}}</div>
    </div>
</template>