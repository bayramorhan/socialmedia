<script setup>
import { Menu, MenuButton, MenuItem, MenuItems } from "@headlessui/vue";

defineProps(["user"]);
</script>

<template>
  <div
    class="hidden md:flex md:min-w-0 md:flex-1 md:items-center md:justify-between"
  >
    <div class="px-8 flex flex-shrink-0 items-center space-x-10 pr-4 w-full">
      <nav aria-label="Global" class="flex space-x-10 flex-1">
        <a
          href="#"
          class="text-sm font-medium text-gray-400 flex hover:text-gray-200 items-center space-x-2.5"
        >
          <div
            class="w-2 h-2 rounded-full ring-1 ring-offset-2 ring-offset-gray-600 bg-gray-400 ring-gray-400"
          ></div>
          <span>Published</span>
        </a>
        <a
          href="#"
          class="text-sm font-medium text-gray-400 flex hover:text-gray-200 items-center space-x-2.5"
        >
          <div
            class="w-2 h-2 rounded-full ring-1 ring-offset-2 ring-offset-gray-600 bg-teal-600 ring-teal-600"
          ></div>
          <span>Scheduled</span>
        </a>
        <a
          href="#"
          class="text-sm font-medium text-gray-400 flex hover:text-gray-200 items-center space-x-2.5"
        >
          <div
            class="w-2 h-2 rounded-full ring-1 ring-offset-2 ring-offset-gray-600 bg-amber-600 ring-amber-600"
          ></div>
          <span>Need Approval</span>
        </a>
        <a
          href="#"
          class="text-sm font-medium text-gray-400 flex hover:text-gray-200 items-center space-x-2.5"
        >
          <div
            class="w-2 h-2 rounded-full ring-1 ring-offset-2 ring-offset-gray-600 bg-red-600 ring-red-600"
          ></div>
          <span>Error</span>
        </a>
        <a
          href="#"
          class="text-sm font-medium text-gray-400 flex hover:text-gray-200 items-center space-x-2.5"
        >
          <div
            class="w-2 h-2 rounded-full ring-1 ring-offset-2 ring-offset-gray-600 bg-sky-600 ring-sky-600"
          ></div>
          <span>Notes</span>
        </a>
      </nav>
      <div class="flex items-center space-x-8">
        <Menu as="div" class="relative inline-block text-left">
          <MenuButton
            class="flex rounded-full bg-white text-sm focus:outline-none focus:ring-2 focus:ring-indigo-600 focus:ring-offset-2"
          >
            <span class="sr-only">Open user menu</span>
            <img class="h-8 w-8 rounded-full" :src="user.imageUrl" alt="" />
          </MenuButton>

          <transition
            enter-active-class="transition ease-out duration-100"
            enter-from-class="transform opacity-0 scale-95"
            enter-to-class="transform opacity-100 scale-100"
            leave-active-class="transition ease-in duration-75"
            leave-from-class="transform opacity-100 scale-100"
            leave-to-class="transform opacity-0 scale-95"
          >
            <MenuItems
              class="absolute right-0 z-10 mt-2 w-56 origin-top-right rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
            >
              <div class="py-1">
                <MenuItem v-slot="{ active }">
                  <a
                    href="#"
                    :class="[
                      active ? 'bg-gray-100' : '',
                      'block px-4 py-2 text-sm text-gray-700',
                    ]"
                    >Your Profile</a
                  >
                </MenuItem>
                <MenuItem v-slot="{ active }">
                  <a
                    href="#"
                    :class="[
                      active ? 'bg-gray-100' : '',
                      'block px-4 py-2 text-sm text-gray-700',
                    ]"
                    >Sign Out</a
                  >
                </MenuItem>
              </div>
            </MenuItems>
          </transition>
        </Menu>
      </div>
    </div>
  </div>
</template>
