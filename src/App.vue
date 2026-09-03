<script setup>
import { ref, provide, watch, onMounted } from "vue";
import PaneRight from "./components/PaneRight.vue";
import { cityProvide, API_ENDPOINT } from "./constants.js";
import PaneLeft from "./components/PaneLeft.vue";

let data = ref();
let error = ref();
let activeIndex = ref(0);
let city = ref("Алматы");
provide(cityProvide, city);

watch(city, () => {
  getCity(city.value);
});

onMounted(() => {
  getCity(city.value);
});

async function getCity(city) {
  const params = new URLSearchParams({
    q: city,
    lang: "ru",
    key: "9e9fff6e50ab40bba25130416260908",
    days: 3,
  });
  const res = await fetch(`${API_ENDPOINT}/forecast.json?${params.toString()}`);
  if (res.status !== 200) {
    error.value = await res.json();
    data.value = null;
    return;
  }
  error.value = null;
  data.value = await res.json();
}
</script>

<template>
  <main class="main">
    <div class="left">
      <PaneLeft
        v-if="data"
        :day-data="data.forecast.forecastday[activeIndex]"
      />
    </div>
    <div class="right">
      <PaneRight
        :data
        :error
        :active-index="activeIndex"
        @select-index="(i) => (activeIndex = i)"
      />
    </div>
  </main>
</template>

<style scoped>
.main {
  display: flex;
  align-items: center;
  justify-content: center;
}
.right {
  background: var(--color-bg-main);
  padding: 60px 50px;
  border-radius: 0 25px 25px 0;
}
.left {
  width: 500px;
  height: 680px;
  border-radius: 30px;
  background-image: url("/public/bg.png");
  background-size: cover;
  background-repeat: no-repeat;
}
</style>
