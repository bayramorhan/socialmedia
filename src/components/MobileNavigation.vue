<script setup>
import { ref } from "vue";
import {
  Dialog,
  DialogPanel,
  TransitionChild,
  TransitionRoot,
} from "@headlessui/vue";
import { MagnifyingGlassIcon } from "@heroicons/vue/20/solid";
import { BellIcon, XMarkIcon } from "@heroicons/vue/24/outline";

defineProps(["user"]);

const navigation = [
  {
    name: "Inboxes",
    href: "#",
    children: [
      { name: "Technical Support", href: "#" },
      { name: "Sales", href: "#" },
      { name: "General", href: "#" },
    ],
  },
  { name: "Reporting", href: "#", children: [] },
  { name: "Settings", href: "#", children: [] },
];

const userNavigation = [
  { name: "Your Profile", href: "#" },
  { name: "Sign out", href: "#" },
];

const mobileMenuOpen = ref(false);

defineExpose({ mobileMenuOpen });
</script>

<template>
  <TransitionRoot as="template" :show="mobileMenuOpen">
    <Dialog
      as="div"
      class="relative z-40 md:hidden"
      @close="mobileMenuOpen = false"
    >
      <TransitionChild
        as="template"
        enter="transition-opacity transform duration-200"
        enter-from="opacity-0"
        enter-to="opacity-100"
        leave="transition-opacity transform duration-200"
        leave-from="opacity-100"
        leave-to="opacity-0"
      >
        <div
          class="hidden sm:fixed sm:inset-0 sm:block sm:bg-gray-600 sm:bg-opacity-75"
        />
      </TransitionChild>

      <div class="fixed inset-0 z-40">
        <TransitionChild
          as="template"
          enter="transition ease-out duration-150 sm:ease-in-out sm:duration-300"
          enter-from="transform opacity-0  sm:translate-x-full sm:opacity-100"
          enter-to="transform opacity-100   sm:translate-x-0 sm:opacity-100"
          leave="transition ease-in duration-150 sm:ease-in-out sm:duration-300"
          leave-from="transform opacity-100  sm:translate-x-0 sm:opacity-100"
          leave-to="transform opacity-0   sm:translate-x-full sm:opacity-100"
        >
          <DialogPanel
            class="fixed inset-0 z-40 h-full w-full bg-white sm:inset-y-0 sm:left-auto sm:right-0 sm:w-full sm:max-w-sm sm:shadow-lg"
            aria-label="Global"
          >
            <div class="flex h-16 items-center justify-between px-4 sm:px-6">
              <a href="#">
                <img
                  class="block h-8 w-auto"
                  src="https://tailwindui.com/img/logos/mark.svg?color=indigo&shade=500"
                  alt="Your Company"
                />
              </a>
              <button
                type="button"
                class="-mr-2 inline-flex items-center justify-center rounded-md p-2 text-gray-400 hover:bg-gray-100 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-600"
                @click="mobileMenuOpen = false"
              >
                <span class="sr-only">Close main menu</span>
                <XMarkIcon class="block h-6 w-6" aria-hidden="true" />
              </button>
            </div>
            <div class="max-w-8xl mx-auto mt-2 px-4 sm:px-6">
              <div class="relative text-gray-400 focus-within:text-gray-500">
                <label for="mobile-search" class="sr-only"
                  >Search all inboxes</label
                >
                <input
                  id="mobile-search"
                  type="search"
                  placeholder="Search all inboxes"
                  class="block w-full rounded-md border-gray-300 pl-10 placeholder-gray-500 focus:border-indigo-600 focus:ring-indigo-600"
                />
                <div
                  class="absolute inset-y-0 left-0 flex items-center justify-center pl-3"
                >
                  <MagnifyingGlassIcon class="h-5 w-5" aria-hidden="true" />
                </div>
              </div>
            </div>
            <div class="max-w-8xl mx-auto py-3 px-2 sm:px-4">
              <template v-for="item in navigation" :key="item.name">
                <a
                  :href="item.href"
                  class="block rounded-md py-2 px-3 text-base font-medium text-gray-900 hover:bg-gray-100"
                  >{{ item.name }}</a
                >
                <a
                  v-for="child in item.children"
                  :key="child.name"
                  :href="child.href"
                  class="block rounded-md py-2 pl-5 pr-3 text-base font-medium text-gray-500 hover:bg-gray-100"
                  >{{ child.name }}</a
                >
              </template>
            </div>
            <div class="border-t border-gray-200 pt-4 pb-3">
              <div class="max-w-8xl mx-auto flex items-center px-4 sm:px-6">
                <div class="flex-shrink-0">
                  <img
                    class="h-10 w-10 rounded-full"
                    :src="user.imageUrl"
                    alt=""
                  />
                </div>
                <div class="ml-3 min-w-0 flex-1">
                  <div class="truncate text-base font-medium text-gray-800">
                    {{ user.name }}
                  </div>
                  <div class="truncate text-sm font-medium text-gray-500">
                    {{ user.email }}
                  </div>
                </div>
                <a
                  href="#"
                  class="ml-auto flex-shrink-0 bg-white p-2 text-gray-400 hover:text-gray-500"
                >
                  <span class="sr-only">View notifications</span>
                  <BellIcon class="h-6 w-6" aria-hidden="true" />
                </a>
              </div>
              <div class="max-w-8xl mx-auto mt-3 space-y-1 px-2 sm:px-4">
                <a
                  v-for="item in userNavigation"
                  :key="item.name"
                  :href="item.href"
                  class="block rounded-md py-2 px-3 text-base font-medium text-gray-900 hover:bg-gray-50"
                  >{{ item.name }}</a
                >
              </div>
            </div>
          </DialogPanel>
        </TransitionChild>
      </div>
    </Dialog>
  </TransitionRoot>
</template>
