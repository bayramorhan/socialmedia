<script setup>
const sidebarNavigation = [
  {
    name: "Atica",
    href: "#",
    logo: "https://uilogos.co/img/logomark/atica.png",
    current: true,
  },
  {
    name: "Hexa",
    href: "#",
    logo: "https://uilogos.co/img/logomark/hexa.png",
    current: false,
  },
  {
    name: "Nira",
    href: "#",
    logo: "https://uilogos.co/img/logomark/nira.png",
    current: false,
  },
  {
    name: "Muszica",
    href: "#",
    logo: "https://uilogos.co/img/logomark/muszica.png",
    current: false,
  },
  {
    name: "Fossa",
    href: "#",
    logo: "https://uilogos.co/img/logomark/fossa.png",
    current: false,
  },
  {
    name: "Solaytic",
    href: "#",
    logo: "https://uilogos.co/img/logomark/solaytic.png",
    current: false,
  },
];
</script>

<template>
  <nav
    aria-label="Sidebar"
    class="hidden md:block md:flex-shrink-0 md:overflow-y-auto md:bg-gray-800"
  >
    <div class="relative flex w-20 flex-col space-y-3 p-3">
      <a
        v-for="item in sidebarNavigation"
        :key="item.name"
        :href="item.href"
        :class="[
          item.current
            ? 'bg-gray-900 text-white'
            : 'text-gray-400 hover:bg-gray-700',
          'flex-shrink-0 inline-flex items-center justify-center h-14 w-14 rounded-lg',
        ]"
      >
        <span class="sr-only">{{ item.name }}</span>
        <img :src="item.logo" class="w-8 h-8" :title="item.name" />
      </a>
    </div>
  </nav>
</template>
