<script setup>
const emit = defineEmits(['onClickRemove'])
defineProps({
  id: Number,
  title: String,
  price: Number,
  imageUrl: String,
  price: Number
})
</script>

<template>
  <div class="gap-4 flex border border-slate-200 p-4 rounded-xl">
    <img class="w-16 h-16" :src="imageUrl" alt="Sneakers" />

    <div class="flex flex-col">
      <p>{{ title }}</p>
      <div class="flex justify-between">
        <b>{{ price }} руб.</b>
      </div>
    </div>
    <img
      @click="emit('onClickRemove')"
      class="opacity-30 hover:opacity-100 cursor-pointer"
      src="/close.svg"
      alt=""
    />
  </div>
</template>
