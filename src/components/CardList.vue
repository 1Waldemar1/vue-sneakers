<script setup>
import Card from './Card.vue'
defineProps({
  items: Array,
})
</script>
<template>
  <div class="grid grid-cols-4 gap-5">
    <Card
      v-for="item in items"
      :key="item.id"
      :imageUrl="item.imageUrl"
      :title="item.title"
      :price="item.price"
      :is-added="false"
      :is-favorite="false"
      :on-click-add="OnClickAdd"
    />
  </div>
</template>
