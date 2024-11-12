<template>
  <div class="fixed inset-0 z-10 bg-black bg-opacity-75"></div>
  <div class="fixed inset-0 flex items-center justify-center z-20">
    <div class="bg-white px-16 justify-center items-center py-14 rounded-md shadow-xl max-w-sm">
      <!-- Ваше содержимое окна -->
      <div class="flex justify-center">
        <h2 class="text-xl font-semibold mb-4">Поздравляем!</h2>
      </div>
      <p class="mb-4">Ваш заказ успешно оформлен!</p>
      <div class="flex justify-center">
        <button
          @click="reloadPage"
          class="px-4 py-2 bg-lime-500 text-white rounded hover:bg-lime-700 transition duration-300"
        >
          Продолжить покупки!
        </button>
      </div>
    </div>
  </div>
</template>

<script setup>
const props = defineProps({
  reloadPage: Function
})
console.log('Вызвана функцияя Alert')
</script>
