<script setup>
    const {label = "Не указано", value} = defineProps({
        label: String,
        value: String
    });
</script>

<template>
    <div class="stat">
        <div class="stat-label">{{ label }}</div>
        <div class="stat-value">{{ value }}</div>
    </div>
</template>

<style scoped>
    .stat {
        font-size: 28px;
        display: flex;
        justify-content: space-between;
        gap: 16px;
    }
    .stat-label {
        font-weight: 700;
        text-transform: uppercase;
    }
    .stat-value {
        font-weight: 500;
    }
</style>