<script setup>
import { computed, provide, ref, watch } from 'vue'
import Drawler from './components/Drawler.vue'
import Header from './components/Header.vue'

const cart = ref([])

const drawlerOpen = ref(false)

const totalPrice = computed(() => cart.value.reduce((acc, item) => acc + item.price, 0))
const vatPrice = computed(() => Math.round((totalPrice.value * 5) / 100))

const closeDrawler = () => {
  drawlerOpen.value = false
}

const openDrawler = () => {
  drawlerOpen.value = true
}

const addToCart = (item) => {
  cart.value.push(item)
  item.isAdded = true
}

const removeFromCart = (item) => {
  cart.value.splice(cart.value.indexOf(item), 1)
  item.isAdded = false
}

watch(
  cart,
  () => {
    localStorage.setItem('cart', JSON.stringify(cart.value))
  },
  { deep: true }
)

provide('cart', {
  cart,
  closeDrawler,
  openDrawler,
  addToCart,
  removeFromCart
})
</script>

<template>
  <Drawler v-if="drawlerOpen" :total-price="totalPrice" :vat-price="vatPrice" />

  <div class="bg-white w-4/5 m-auto rounded-xl shadow-xl mt-14">
    <Header :total-price="totalPrice" @open-drawler="openDrawler" />

    <div class="p-10">
      <router-view></router-view>
    </div>
  </div>
</template>

<style scoped></style>
