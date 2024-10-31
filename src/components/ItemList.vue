<script setup>
import Item from './Item.vue'

defineProps({
  items: Array
})
</script>

<template>
  <div class="grid grid-cols-4 gap-5 mt-5">
    <Item
      title="Мужские Кроссовки Nike Blazer"
      imageUrl="/sneakers/sneakers-1.jpg"
      :price="5000"
      isFavourite="false"
      :onClickAdd="onClickAdd"
      :isAdded="true"
    />
  </div>
</template>
