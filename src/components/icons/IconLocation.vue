<template>
    <svg 
        xmlns="http://www.w3.org/2000/svg" 
        viewBox="0 0 16 16"
        class="icon"
        :style="{ height: size, width: size }"
    >
        <path fill="currentColor" fill-rule="evenodd" d="M12.5 6a4.47 4.47 0 0 1-.883 2.677L8 13.5L4.383 8.677A4.5 4.5 0 1 1 12.5 6ZM14 6c0 1.34-.439 2.576-1.18 3.574L8.937 14.75L8 16l-.938-1.25L3.18 9.574A6 6 0 1 1 14 6ZM8 8a2 2 0 1 0 0-4a2 2 0 0 0 0 4Z" clip-rule="evenodd"/>
    </svg>
</template>

<script setup>
defineProps({
    size: {
        type: String,
        default: '24px'
    }
})
</script>

<style scoped>
.icon {
    display: inline-block;
    vertical-align: middle;
}
</style>
