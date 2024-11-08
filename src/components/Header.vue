<script setup>
const emit = defineEmits(['openDrawer'])
</script>

<template>
  <header class="flex justify-between border-b border-slate-300 px-8 py-8">
    <div class="flex items-center">
      <img src="/logo.png" alt="logo" class="w-10 mr-5 hover:scale-125" />
      <div>
        <h2 class="text-xl font-bold uppercase">The Tяги</h2>
        <p class="text-slate-500">Магазин лучших кроссовок</p>
      </div>
    </div>

    <ul class="flex items-center gap-10">
      <li @click="() => emit('openDrawer')" class="flex-items-center gap-3 cursor-pointer">
        <img src="/cart.svg" alt="" />
        <b class="text-slate-500 hover:text-black">1200 руб</b>
      </li>
      <li class="flex-items-center gap-3 cursor-pointer">
        <img src="/heart.svg" alt="" />
        <span class="text-slate-400 hover:text-black">Избранное</span>
      </li>
      <li class="flex-items-center gap-3 cursor-pointer">
        <img src="/profile.svg" alt="" />
        <span class="text-slate-400 hover:text-black">Профиль</span>
      </li>
    </ul>
  </header>
</template>
