<script setup>
import { onMounted, ref, watch, reactive, provide, computed } from 'vue'

import Header from './components/Header.vue'
import ItemList from './components/ItemList.vue'
import Drawer from './components/Drawer.vue'
import axios from 'axios'

const items = ref([])
const cart = ref([])
const cartItems = ref([])

const total = computed(() => cart.value.reduce((acc, item) => acc + item.price, 0))
const drawerOpen = ref(false)
const closeDrawer = () => {
  drawerOpen.value = false
}

const openDrawer = () => {
  drawerOpen.value = true
}
const filters = reactive({
  sortBy: 'title',
  searchQuery: ''
})

const addToCart = (item) => {
  cart.value.push(item)
  item.isAdded = true
}
const removeFromCart = (item) => {
  cart.value.splice(cart.value.indexOf(item), 1)
  console.log('hueta')
  item.isAdded = false
}
const onClickAddPlus = (item) => {
  if (!item.isAdded) {
    cart.value.push(item)
    item.isAdded = true
    console.log(item)
  } else {
    cart.value.splice(cart.value.indexOf(item), 1)
    item.isAdded = false
  }
}
const onChangeSelect = (event) => {
  filters.sortBy = event.target.value
}

const onChangeSearch = (event) => {
  filters.searchQuery = event.target.value
}

const fetchFavorites = async () => {
  try {
    const { data } = await axios.get('https://ce3e5379497a47dc.mokky.dev/favorites')
    items.value = items.value.map((item) => {
      const favorite = favorites.find((favorite) => favorite.parentId === item.id)
      if (!favorite) {
        return item
      }
      return {
        ...item,
        isFavorite: true,
        favoriteId: favorite.id
      }
    })
  } catch (err) {
    console.log(err)
  }
}
const addToFavorite = async (item) => {
  item.isFavorite = true
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
    items.value = data.map((obj) => ({
      ...obj,
      isFavorite: false,
      isAdded: false
    }))
  } catch (err) {
    console.log(err)
  }
}
onMounted(async () => {
  await fetchItems()
  await fetchFavorites()
})
watch(filters, fetchItems)

provide('cart', {
  cart,
  closeDrawer,
  openDrawer,
  onClickAddPlus,
  addToCart,
  removeFromCart
})
</script>
<template>
  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-10">
    <Drawer :total="total" v-if="drawerOpen" />
    <Header :total="total" @openDrawer="openDrawer" />
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

      <ItemList :items="items" @add-to-cart="onClickAddPlus" />
    </div>
  </div>
</template>

<style scoped></style>
