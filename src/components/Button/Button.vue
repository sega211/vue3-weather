<script setup>

</script>
<template>
    <button class="button">
        <div>
            <slot name="icon"></slot>
        </div>
        <slot />
    </button>
</template>
<style scoped>
    .button {
        border: none;
        border-radius: 10px;
        padding: 14px;
        background: var(--color-gradient);
        cursor: pointer;
        font-family: var(--font);
        font-size: 20px;
        font-weight: 600;
        color: var(--color-primary);
        display: flex;
        gap: 9px;
        align-items: center;
        height: 53px;
        width: 100%;
        justify-content: center
    }
    .button:hover {
        background: var(--color-gradient-inverted);
    }

</style>