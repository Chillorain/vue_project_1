<script setup>
    import Button from './Button.vue'
    import Input from './Input.vue'
    import { ref } from 'vue'
    import IconLocation from '../icons/IconLocation.vue'

    const emit = defineEmits({
        changeCity(payload) {
            return payload;
        }
    })
    
    let city = ref("Almaty");
    let isEdited = ref(false);

    function select() {
        isEdited.value = false;
        emit('changeCity', 'Astana')
    }

    function edit() {
        isEdited.value = true;
    }
</script>

<template>
    <div class="city-select">
        {{ city }}
        <div v-if="isEdited" class="city-input">
            <Input  v-model="city" placeholder="Введите город" />
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