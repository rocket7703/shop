<script setup>
import { onMounted, ref, watch, reactive } from 'vue'

import Header from './components/Header.vue'
import ItemList from './components/ItemList.vue'
import Drawer from './components/Drawer.vue'
import axios from 'axios'

const items = ref([])
const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
})

const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const onChangeSearch = (event) => {
  filters.searchQuery = event.target.value
}

const fetchItems = async () => {
  try {
    const params = {
      sortBy: filters.sortBy
    }
    if (filters.searchQuery) {
      params.title = `*${filters.searchQuery}*`
    }
    const { data } = await axios.get('https://ce3e5379497a47dc.mokky.dev/items', {
      params
    })
    items.value = data
  } catch (err) {
    console.log(err)
  }
}
onMounted(fetchItems)
watch(filters, fetchItems)
</script>
<template>
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <!-- <Drawer /> -->
    <Header />
    <div class="p-10">
      <div class="flex justify-between items-center">
        <h2 class="m-2 text-3xl font-bold">Все кроссовки</h2>
        <div class="flex gap-4">
          <select @change="onChangeSelect" class="py-2 px-3 border rounded-md outline-none">
            <option value="name">По названию</option>
            <option value="price">Сначала дешёвые</option>
            <option value="-price">Сначала дорогие</option>
          </select>
          <div class="relative">
            <img class="absolute left-4 top-3" src="/search.svg" alt="" />
            <input
              @input="onChangeSearch"
              class="outline-none focus:border-gray-400 border rounded-nd py-2 pl-10 pr-4"
              type="text "
              placeholder="Поиск..."
            />
          </div>
        </div>
      </div>

      <ItemList :items="items" />
    </div>
  </div>
</template>

<style scoped></style>
