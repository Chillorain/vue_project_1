<script setup>
import { ref, computed } from 'vue';
import CitySelect from './components/citySelect.vue';
import Stat from './components/Stat.vue'

let savedcity = ref('Almaty');
let data = ref({
  humidity: 90,
  rain: 0,
  wind: 3
});

const dataModified = computed(() => {
  return [
    {
      label: 'Влажность',
      stat: data.value.humidity + '%'
    },
    {
      label: 'Осадки',
      stat: data.value.rain + '%'
    },
    {
      label: 'Ветер',
      stat: data.value.wind + ' м/ч'
    }
  ];
});

function getCity(city) {
  savedcity.value = city;
  data.value.humidity = 20;
}
</script>

<template>
  <main class="main">
    <div id="city">{{ savedcity }}</div>
    <Stat v-for="item in dataModified" v-bind="item" :key="item.label" />
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