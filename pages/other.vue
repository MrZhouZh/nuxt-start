<script setup lang="ts">
definePageMeta({
  middleware: 'other'
})
const open = ref(false)
</script>

<template>
  <p>
    The layout is set within <code>middleware/other.ts</code>
  </p>
  <button @click="open = !open">{{ open ? 'Close' : 'Open' }} Modal</button>
  <Teleport to="body">
    <div v-if="open" class="modal">
      <p>This is a modal</p>
      <button @click="open = false">Close</button>
    </div>
  </Teleport>
</template>
