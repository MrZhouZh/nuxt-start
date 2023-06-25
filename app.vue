<script setup lang="ts">
useHead({
  titleTemplate: '%s - Meta tags'
})
</script>

<template>
  <div>
    <NuxtLoadingIndicator />
    <nav>
      <NuxtLink to="/">Home</NuxtLink>
      <NuxtLink to="/custom">Custom</NuxtLink>
      <NuxtLink to="/dynamic">Dynamic</NuxtLink>
      <NuxtLink to="/other">Other</NuxtLink>
      <NuxtLink to="/component">Component</NuxtLink>
      <NuxtLink to="/external">External</NuxtLink>
      <NuxtLink to="/about">About</NuxtLink>
    </nav>
    <NuxtLayout class="layouts">
      <NuxtPage />
    </NuxtLayout>
    <footer>
      <button @click="setPageLayout('default')">layouts/default.vue</button>
      <button @click="setPageLayout('custom')">layouts/custom.vue</button>
      <button @click="setPageLayout('other')">layouts/other.vue</button>
      <button @click="setPageLayout('')">Remove layout</button>
    </footer>
  </div>
</template>

<style>
body.my-body-class {
  background-color: #eee;
}
</style>

<style scoped>
nav, footer {
  display: flex;
  align-items: center;
  gap: 1rem;
  padding: 1rem;
}

.layouts {
  padding: 1rem;
}
</style>
