<script setup>
    const data = defineModel({ type: String, required: true });
</script>

<template>
    <input v-model="data" class="input" />
</template>

<style scoped>
    .input {
        color: var(--color-primary);
        width: 260px;
        height: 53px;
        border-radius: 10px;
        border: none;
        padding: 15px 20px;
        font-size: 18px;
        box-shadow: 1px 2px 4px 0px var(--color-bg-main);
        background: var(--color-card-bg);
    }
    .input::placeholder {
        color: var(--color-text-placeholder);
    }
</style>