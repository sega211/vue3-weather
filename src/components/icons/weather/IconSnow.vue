<script setup>
    const {color = 'white', size = 54} = defineProps({ 
        color: String,
        size: Number
    })
</script>

<template>
  <svg 
    xmlns="http://www.w3.org/2000/svg" 
    :width="size" 
    :height="size" 
    viewBox="0 0 24 24"
    :style="{ color: color, scale: size / 54 }"  
  >
    <path 
      fill="currentColor" 
      stroke="currentColor" 
      stroke-linecap="round" 
      stroke-linejoin="round" 
      d="M18.5 18.67c0 1.29-1 2.33-2.25 2.33S14 19.96 14 18.67c0-1.55 2.25-4.17 2.25-4.17s2.25 2.62 2.25 4.17M4 17.36c-.14-.54.18-1.11.73-1.25L7 15.5l-1.67-1.64c-.4-.4-.4-1.05 0-1.46c.4-.4 1.07-.4 1.46 0l1.66 1.65l.59-2.25c.14-.56.71-.88 1.25-.73c.56.14.88.71.71 1.26l-.58 2.25l2.25-.58a.99.99 0 0 1 1.26.71c.15.54-.17 1.11-.73 1.25l-2.25.59l1.65 1.66c.4.39.4 1.06 0 1.46c-.4.4-1.06.4-1.45 0L9.5 18l-.61 2.27c-.14.56-.71.87-1.25.73c-.56-.14-.87-.71-.73-1.26l.59-2.24l-2.24.59c-.55.14-1.12-.17-1.26-.73M1 11a5 5 0 0 1 5-5c1-2.35 3.3-4 6-4c3.43 0 6.24 2.66 6.5 6.03L19 8a4 4 0 0 1 4 4a4 4 0 0 1-4 4a1 1 0 0 1-1-1a1 1 0 0 1 1-1a2 2 0 0 0 2-2a2 2 0 0 0-2-2h-2V9a5 5 0 0 0-5-5C9.5 4 7.45 5.82 7.06 8.19C6.73 8.07 6.37 8 6 8a3 3 0 0 0-3 3c0 .85.35 1.61.91 2.16c.36.39.35 1-.03 1.38a.996.996 0 0 1-1.41 0A4.988 4.988 0 0 1 1 11Z"
    />
  </svg>

</template>

<style scoped>

</style>