<script setup>
let counter = ref(0);

setInterval(() => {
  counter.value++;
}, 1000);
</script>

<template>
  <router-view />
</template>
