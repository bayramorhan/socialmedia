<script setup>
import DefaultLayout from "../layouts/DefaultLayout.vue";
useHead({
  title: "sociality.io",
});
</script>

<template>
  <default-layout>
    <template #actions>
      <actions-list></actions-list>
    </template>
    <template #default>
      <div>
        <Suspense>
          <template #default>
            <cards />
          </template>
          <template #fallback>
            <p class="py-10 pl-10">Loading your cards, please be patient...</p>
          </template>
        </Suspense>
      </div>
    </template>
  </default-layout>
</template>
