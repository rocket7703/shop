<script setup>
import DrawerHead from './DrawerHead.vue'
import Cardlist from './Cardlist.vue'
</script>
<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-50"></div>
  <div class="bg-white w-96 h-full fixed z-20 right-0 top-0 p-3">
    <DrawerHead />
    <Cardlist />

    <div>
      <div class="flex gap-2 mb-5">
        <span>Итого:</span>
        <div class="flex-1 border-b border-dashed"></div>

        <b>4 700 руб</b>
      </div>

      <button
        class="bg-lime-500 hover:bg-lime-600 active:bg-lime-700 text-white w-10/12 rounded-xl py-3 mx-8"
      >
        Купить
      </button>
    </div>
  </div>
</template>
