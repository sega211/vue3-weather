<script setup>
    const {label, stat} = defineProps({
        label: String,
        stat: String
    });
</script>
<template>
    <div class="stat">
        <div class="stat-name">
            {{ label }}
        </div>
        <div class="stat-value">{{ stat }}</div>
    </div>
</template>
<style scoped>
    .stat {
        display: flex;
        align-items: center;
        justify-content: space-between;
        font-size: 28px;
        gap: 16px;
    }
    .stat-name {
        
        font-weight: 700;
        text-transform: uppercase;
    }
    .stat-value {
        
        font-weight: 500;
    }
</style>