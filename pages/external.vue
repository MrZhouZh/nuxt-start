<script setup lang="ts">
type Product = {
  brand: string
  category: string
  description: string
  discountPercentage: number
  id: number
  images: string[]
  price: number
  rating: number
  stock: number
  thumbnail: string
  title: string
}
const id = ref(1)
const { data: product, pending, error } = await useFetch<Product>(() => `https://dummyjson.com/products/${id.value}`)

/* Same as:
const { data: product, pending, error } = await useAsyncData(() => {
  return $fetch(`https://dummyjson.com/products/${id.value}`)
}, {
  watch: [id]
})
*/
</script>

<template>
  <div>
    <p>Result of <code>https://dummyjson.com/products/</code><input type="number" v-model="id" /></p>
    <p><button @click="id--">Previous</button> - <button @click="id++">Next</button></p>
    <p v-if="pending">Fetching...</p>
    <pre v-else-if="error">{{ error }}</pre>
    <pre v-else>{{ product }}</pre>
    <NuxtLink to="/">Back home</NuxtLink>
  </div>
</template>
