<script setup>
import CitySelect from './components/citySelect.vue';
import Stat from './components/Stat.vue'
const data = {
  label: "Влажность",
  value: "90%"
}

function getCity(city) {
  console.log(city)
}
</script>

<template>
  <main class="main">
    <Stat v-bind="data" />
    <Stat label="Осадки" value="0%" />
    <CitySelect @change-city="getCity" />
  </main>
</template>

<style scoped>
  .main {
    background: var(--color-bg-main);
    padding: 60px 50px;
    border-radius: 10%;
  }
</style>