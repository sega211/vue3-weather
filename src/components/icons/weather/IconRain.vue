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
      d="M6 14.03a1 1 0 0 1 1 1c0 .55-.45 1-1 1c-2.76 0-5-2.24-5-5s2.24-5 5-5c1-2.35 3.3-4 6-4c3.43 0 6.24 2.66 6.5 6.03l.5-.03a4 4 0 0 1 4 4c0 2.2-1.79 4-4 4h-1c-.55 0-1-.45-1-1c0-.56.45-1 1-1h1a2 2 0 0 0 2-2a2 2 0 0 0-2-2h-2v-1c0-2.76-2.24-5-5-5c-2.5 0-4.55 1.81-4.94 4.18c-.33-.12-.69-.18-1.06-.18a3 3 0 0 0-3 3a3 3 0 0 0 3 3m6 .12c.18.24.37.51.56.79C13 15.56 14 17.03 14 18a2 2 0 0 1-2 2a2 2 0 0 1-2-2c0-.97 1-2.44 1.44-3.06c.19-.28.38-.54.56-.79m0-3.12l-.5.56s-.85.96-1.71 2.22C8.93 15.06 8 16.56 8 18a4 4 0 0 0 4 4a4 4 0 0 0 4-4c0-1.44-.93-2.94-1.79-4.19c-.86-1.26-1.71-2.22-1.71-2.22"
    />
  </svg>
 
</template>

<style scoped>

</style>