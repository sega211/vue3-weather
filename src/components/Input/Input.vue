<script setup>
    const data = defineModel({
        type: String
    })
</script>
<template>
    <input v-model="data" class="input" />
</template>
<style scoped>
    .input {
        color: var(--color-primary);
        width: 260px;
        border: none;
        border-radius: 10px;
        background: var(--color-bg-card);
        box-shadow: 1px 2px 4px var(--color-bg-main);
        height: 53px;
        font-size: 18px;
        padding: 15px 20px;
    }
    .input::placeholder {
        color: var(--color-text-placeholder);
    }
</style>