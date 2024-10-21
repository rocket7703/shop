<script setup>
defineProps ({
    imageUrl:String,
})
</script>

<template>
    <div>
    <div class="relative   bg-white border border-slate-100 rounded-3xl p-8 cursor-pointer transition hover:-translate-y-2 scale-105 hover:shadow-xl">
 <img src="/like-2.svg" alt="like 1" class="absolute top-8 left-8">
 <img :src="imageUrl" alt="Sneaker">
 <p> Мужские кроссовки Nike Blazer Mid Suede</p>
 <div class="flex justify-between">
   <div class="flex flex-col ">
    <span class="text-slate-500">Цена:</span>
    <span>4700 руб</span>
    
   </div>
   <img  src="/plus.svg" alt="Plus">
 </div>
    </div>
  </div>
</template>