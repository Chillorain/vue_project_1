<script setup>
import Button from "./Button.vue";
import Input from "./Input.vue";
import { ref, onMounted } from "vue";
import IconLocation from "../icons/IconLocation.vue";

const emit = defineEmits({
  "select-city"(payload) {
    return payload;
  },
});

let city = ref("Almaty");
let isEdited = ref(false);

onMounted(() => {
  emit("select-city", city.value);
});

function select() {
  isEdited.value = false;
  emit("select-city", city.value);
}

function edit() {
  isEdited.value = true;
}
</script>

<template>
  <div class="city-select">
    <div v-if="isEdited" class="city-input">
      <Input
        v-model="city"
        v-focus
        placeholder="Введите город"
        @keyup.enter="select()"
      />
      <Button @click="select()">Сохранить</Button>
    </div>
    <Button v-else @click="edit()">
      <IconLocation />
      Изменить город
    </Button>
  </div>
</template>

<style scoped>
.city-select {
  width: 420px;
}

.city-input {
  display: flex;
  gap: 12px;
  width: 420px;
}
</style>
