<script setup>
const cards = await import("../data/cards.json");
</script>

<template>
  <div class="p-6 space-y-10">
    <div v-for="(card, key) in cards.posts_by_date" :key="key">
      <h2 class="text-gray-400 border-b border-gray-600 pb-2 mb-6 text-lg">
        {{ key }}
      </h2>
      <div class="grid grid-cols-3 gap-6">
        <Card
          v-for="cardItem in card"
          :item="cardItem"
          :key="cardItem.created_at"
        />
      </div>
    </div>
  </div>
</template>
