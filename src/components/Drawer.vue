<script setup>
import DrawerHead from './DrawerHead.vue'
import CartItem from './CartItem.vue'
</script>
<template>
  <div class="fixed top-0 left-0 h-full w-full bg-black z-10 opacity-50"></div>
  <div class="bg-white w-96 h-full fixed z-20 right-0 top-0">
    <DrawerHead />
    <CartItem />
    <CartItem />
    <CartItem />
    <CartItem />
  </div>
</template>
