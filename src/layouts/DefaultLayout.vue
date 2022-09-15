<template>
  <div class="flex h-full flex-col">
    <!-- Top nav-->
    <top-navigation></top-navigation>
    <!-- Bottom section -->
    <div class="flex min-h-0 flex-1 overflow-hidden">
      <!-- Narrow sidebar-->
      <narrow-sidebar></narrow-sidebar>

      <!-- Main area -->
      <main class="min-w-0 flex-1 bg-gray-700 border-t border-gray-700 lg:flex">
        <!-- Primary column -->
        <section
          aria-labelledby="primary-heading"
          class="flex h-full min-w-0 flex-1 flex-col overflow-y-auto lg:order-last"
        >
          <slot />
        </section>

        <!-- Actions column (hidden on smaller screens) -->
        <aside class="hidden lg:order-first lg:block lg:flex-shrink-0">
          <div
            class="relative flex h-full w-60 flex-col overflow-y-auto border-r border-gray-700 bg-gray-100"
          >
            <slot name="actions" />
          </div>
        </aside>
      </main>
    </div>
  </div>
</template>
