<script setup>
import Item from './Item.vue'

defineProps({
  items: Array
})

const emit = defineEmits('addToCart')
</script>

<template>
  <div class="grid grid-cols-4 gap-5 mt-5">
    <Item
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :img="item.imageUrl"
      :price="item.price"
      :id="item.id"
      :isLiked="item.isFavorite"
      :onClickAdd="() => emit('addToCart', item)"
      :isAdded="true"
    />
  </div>
</template>
