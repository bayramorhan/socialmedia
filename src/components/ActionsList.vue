<script setup>
import { PlusSmallIcon, MinusSmallIcon } from "@heroicons/vue/24/outline/";
const menuItems = ref([
  {
    name: "Notifications",
    icon: "",
    isActive: false,
  },
  {
    name: "Summary",
    icon: "",
    isActive: false,
  },
  {
    name: "Publish",
    icon: "",
    isActive: false,
    children: [
      {
        name: "Compose",
        icon: "",
      },
      {
        name: "Feed",
        icon: "",
      },
    ],
  },
  {
    name: "Engage",
    icon: "",
    isActive: false,
  },
  {
    name: "Listen",
    icon: "",
    isActive: false,
  },
  {
    name: "Report",
    icon: "",
    isActive: false,
  },
]);

const toggleHandler = (clickedItem) => {
  if (clickedItem.isActive) {
    clickedItem.isActive = false;
  } else {
    menuItems.value = menuItems.value.map((m) => {
      return { ...m, isActive: false };
    });
    menuItems.value.find(
      (item) => item.name === clickedItem.name
    ).isActive = true;
  }
};
</script>

<template>
  <div class="bg-gray-800 border-l border-gray-700 h-full">
    <ul class="mt-2 divide-y divide-gray-700 text-sm font-medium">
      <TransitionGroup
        mode="out-in"
        enter-active-class="transition-duration-200"
        enter-from-class="opacity-0"
        enter-to-class="opacity-100"
      >
        <li
          v-for="menuItem in menuItems"
          :key="menuItem.name"
          class="cursor-pointer group"
          @click="toggleHandler(menuItem)"
        >
          <div
            class="flex justify-between items-center hover:text-gray-100 p-4"
            :class="[
              menuItem.isActive
                ? 'text-gray-200 bg-indigo-500'
                : 'text-gray-400 ',
            ]"
          >
            <span>{{ menuItem.name }}</span>
            <PlusSmallIcon
              class="w-4"
              v-if="menuItem.children && !menuItem.isActive"
            />
            <MinusSmallIcon
              class="w-4"
              v-else-if="menuItem.children && menuItem.isActive"
            />
          </div>
          <Transition
            enter-active-class="transition duration-100 "
            enter-from-class="opacity-0 "
            enter-to-class="opacity-100 "
            leave-active-class="transition duration-200 transform "
            leave-from-class="opacity-100 translate-y-0"
            leave-to-class="opacity-0 -translate-y-2"
            mode="out-in"
          >
            <div
              v-if="menuItem.children && menuItem.isActive"
              class="pl-6 text-sm font-medium bg-gray-900"
            >
              <ul class="divide-y divide-gray-700 text-gray-400">
                <li
                  v-for="child in menuItem.children"
                  class="py-3.5 hover:text-gray-200"
                >
                  {{ child.name }}
                </li>
              </ul>
            </div>
          </Transition>
        </li>
      </TransitionGroup>
    </ul>
  </div>
</template>
