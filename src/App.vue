<script setup>
import Header from './components/Header.vue'
import ItemList from './components/ItemList.vue'
import Drawer from './components/Drawer.vue'
</script>
<template>
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <!-- <Drawer /> -->
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="m-2 text-3xl font-bold">Все кроссовки</h2>
        <div class="flex gap-4">
          <select class="py-2 px-3 border rounded-md outline-none">
            <option>По названию</option>
            <option>Сначала дешёвые</option>
            <option>Сначала дорогие</option>
          </select>
          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="" />
            <input
              class="outline-none focus:border-gray-400 border rounded-nd py-2 pl-10 pr-4"
              type="text "
              placeholder="Поиск..."
            />
          </div>
        </div>
      </div>

      <ItemList />
    </div>
  </div>
</template>

<style scoped></style>
