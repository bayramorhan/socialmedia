<script setup>
import { Bars3Icon, TrashIcon } from "@heroicons/vue/24/outline";
defineProps(["item"]);
</script>

<template>
  <div
    class="bg-gray-800 shadow rounded px-4 pt-6 pb-10 hover:shadow-lg relative"
  >
    <div class="absolute right-6 top-6 flex items-center space-x-2">
      <TrashIcon class="w-4 text-gray-400 hover:text-red-500 cursor-pointer" />
      <Bars3Icon class="w-5 text-gray-400 hover:text-gray-200 cursor-pointer" />
    </div>
    <datetime class="text-xs text-gray-300 block mb-6">{{
      item.created_at
    }}</datetime>
    <p class="text-sm text-gray-300 mb-5">{{ item.entry.message }}</p>
    <img
      :src="item.entry.image"
      onerror="this.onerror=null;this.src='/img/no-post-image.png';"
      class="w-full object-cover h-56"
      alt=""
    />
  </div>
</template>
