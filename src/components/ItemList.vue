<script setup>
import Item from './Item.vue'

defineProps({
  items: Array
})
</script>

<template>
  <div class="grid grid-cols-4 gap-5 mt-5">
    <Item
      v-for="item in items"
      :key="item.id"
      :title="item.title"
      :img="item.imageUrl"
      :price="item.price"
      isFavourite="true"
      :onClickAdd="onClickAdd"
      :isAdded="true"
    />
  </div>
</template>
