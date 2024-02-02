<script setup>
defineProps({
  totalPrice: Number
})
const emit = defineEmits(['openDrawler'])
</script>

<template>
  <header
    class="lg:flex lg:justify-between lg:border-b border-slate-200 lg:items-center px-10 py-10"
  >
    <router-link to="/"
      ><div class="flex items-center gap-4">
        <img src="/logo.png" alt="Logo" class="w-14" />
        <div>
          <h2 class="text-xl font-bold lg:uppercase">Vue Prokopov</h2>
          <p class="text-slate-400">Магазин лучших кроссовок</p>
        </div>
      </div></router-link
    >

    <ul class="flex items-center gap-10 pt-4 pl-0">
      <li
        @click="() => emit('openDrawler')"
        class="flex items-center cursor-pointer gap-3 lg:gap-3 text-gray-500 hover:text-black"
      >
        <img src="/cart.svg" alt="Cart" />
        <b class="flex flex-col">{{ totalPrice }}₽</b>
      </li>
      <router-link to="/Favorites">
        <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
          <img src="/heart.svg" alt="Cart" />
          <span>Закладки</span>
        </li></router-link
      >
      <li class="flex items-center cursor-pointer gap-3 text-gray-500 hover:text-black">
        <img src="/profile.svg" alt="Cart" />
        <span>Профиль</span>
      </li>
    </ul>
  </header>
</template>
