<script setup>
import Header from './components/Header.vue'
import ItemList from './components/ItemList.vue'

</script>
<template>
  <div class="bg-white w-4/5 m-auto  rounded-xl shadow-xl mt-10">
    <Header />
    <div class="p-10">
    <h2 class=" m-2 text-3xl font-bold">Все кроссовки</h2>
    <ItemList />
 </div>
</div>
</template>

<style scoped></style>
