<script setup lang="ts">
type Todo = {
  id: number
  todo: string
  completed: boolean
  userId: number
}
const todo = ref()
const pending = ref()
const error = ref()

async function randomTodo() {
  pending.value = true
  const data = await useFetch<Todo>(() => `https://dummyjson.com/todos/random`)
  console.log(data, 'useReFetch');
  

  todo.value = data.data
  pending.value = unref(data.pending)
  error.value = unref(data.error)
}
useSeoMeta({
  title: 'About page',
  description: 'This is the about page'
})
onMounted(() => {
  randomTodo()
})
</script>

<template>
  <section>
    <p>This page will be displayed at the /about route.</p>
    <p>
      Result of <code>https://dummyjson.com/todo/random</code>
      <button class="btn" @click="randomTodo">Random</button>
    </p>
    <p v-if="pending">Fetching...</p>
    <div v-else-if="error">
      <pre>{{ error }}</pre>
      <button @click="randomTodo">Try Again...</button>
    </div>
    <pre v-else>{{ todo }}</pre>
  </section>
</template>

<style scoped>
.btn {
  margin-left: 4px;
}
</style>
