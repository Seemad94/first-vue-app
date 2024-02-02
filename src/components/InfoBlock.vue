<script setup>
defineProps({
  title: String,
  description: String,
  imageUrl: String
})
</script>

<template>
  <div class="flex flex-col items-center text-center lg:w-72 mx-auto mt-20">
    <img
      class:height="60"
      width="60"
      lg:height="80"
      lg:width="80"
      :src="imageUrl"
      alt="Info image"
    />
    <h2 class="mt-4 text-base lg:text-2xl font-medium">{{ title }}</h2>
    <p class="text-gray-400 mt-2 text-base">{{ description }}</p>
  </div>
</template>
