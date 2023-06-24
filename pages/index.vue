<script setup lang="ts">
const { data } = await useFetch('/api/hello')

</script>

<template>
  <div>
    <p>Result of <code>/api/hello</code>:</p>
    <pre>{{ data }}</pre>
  </div>
</template>
