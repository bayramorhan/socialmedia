<script setup>
import { ChevronDownIcon } from "@heroicons/vue/20/solid";
import {
  ArchiveBoxIcon,
  Bars3Icon,
  FlagIcon,
  InboxIcon,
  NoSymbolIcon,
  PencilSquareIcon,
  UserCircleIcon,
} from "@heroicons/vue/24/outline";

const sidebarNavigation = [
  { name: "Published", href: "#", icon: InboxIcon, current: true },
  { name: "Scheduled", href: "#", icon: ArchiveBoxIcon, current: false },
  { name: "Need Approval", href: "#", icon: UserCircleIcon, current: false },
  { name: "Error", href: "#", icon: FlagIcon, current: false },
  { name: "Notes", href: "#", icon: NoSymbolIcon, current: false },
];

const user = {
  name: "Whitney Francis",
  email: "whitney.francis@example.com",
  imageUrl:
    "https://images.unsplash.com/photo-1517365830460-955ce3ccd263?ixlib=rb-1.2.1&ixid=eyJhcHBfaWQiOjEyMDd9&auto=format&fit=facearea&facepad=2&w=256&h=256&q=80",
};

const mobileMenuRef = ref();

const mobileMenuButtonHandler = () => {
  mobileMenuRef.value.mobileMenuOpen = true;
};
</script>

<template>
  <header class="relative flex h-16 flex-shrink-0 items-center bg-gray-800">
    <!-- Logo area -->
    <div class="absolute inset-y-0 left-0 md:static md:flex-shrink-0">
      <a
        href="#"
        class="flex h-16 w-16 items-center justify-center bg-gray-900 focus:outline-none focus:ring-0 md:w-20"
      >
        <img
          class="h-8 w-auto"
          src="https://tailwindui.com/img/logos/mark.svg?color=white"
          alt="Your Company"
        />
      </a>
    </div>

    <!-- Picker area -->
    <div class="mx-auto md:hidden">
      <div class="relative">
        <label for="inbox-select" class="sr-only">Choose inbox</label>
        <select
          id="inbox-select"
          class="rounded-md border-0 bg-none pl-3 pr-8 text-base font-medium text-gray-900 focus:ring-2 focus:ring-indigo-600"
        >
          <option
            v-for="item in sidebarNavigation"
            :key="item.name"
            :selected="item.current"
          >
            {{ item.name }}
          </option>
        </select>
        <div
          class="pointer-events-none absolute inset-y-0 right-0 flex items-center justify-center pr-2"
        >
          <ChevronDownIcon class="h-5 w-5 text-gray-500" aria-hidden="true" />
        </div>
      </div>
    </div>

    <!-- Menu button area -->
    <div
      class="absolute inset-y-0 right-0 flex items-center pr-4 sm:pr-6 md:hidden"
    >
      <!-- Mobile menu button -->
      <button
        type="button"
        class="-mr-2 inline-flex items-center justify-center rounded-md p-2 text-gray-400 hover:bg-gray-100 hover:text-gray-500 focus:outline-none focus:ring-2 focus:ring-inset focus:ring-indigo-600"
        @click="mobileMenuButtonHandler"
      >
        <span class="sr-only">Open main menu</span>
        <Bars3Icon class="block h-6 w-6" aria-hidden="true" />
      </button>
    </div>

    <!-- Desktop nav area -->
    <desktop-navigation :user="user"></desktop-navigation>

    <!-- Mobile menu, show/hide this `div` based on menu open/closed state -->
    <mobile-navigation :user="user" ref="mobileMenuRef"></mobile-navigation>
  </header>
</template>
