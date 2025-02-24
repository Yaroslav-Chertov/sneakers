<script setup>
import Card from './Card.vue'

defineProps({
  items: Array,
})

const emit = defineEmits(['addToFavorite', 'addToCart'])
</script>

<template>
  <div class="grid grid-cols-4 gap-5 pr-10 pl-10 pb-10" v-auto-animate>
    <Card
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :id="item.id"
      :imageUrl="item.imageUrl"
      :price="item.price"
      :onClickFavorite="() => emit('addToFavorite', item)"
      :onClickAdd="() => emit('addToCart', item)"
      :isFavorite="item.isFavorite"
      :isAdded="item.isAdded"
    />
  </div>
</template>
