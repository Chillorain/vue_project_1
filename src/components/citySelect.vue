<script setup>
    import Button from './Button.vue'
    import IconLocation from '../icons/IconLocation.vue'

    const emit = defineEmits({
        changeCity(payload) {
            return payload;
        }
    })
    
    function change() {
        emit('changeCity', 'Astana')
    }
</script>

<template>
    <Button @click="change()">
        <IconLocation />
        Изменить город
    </Button>
    <input />
    <Button>Сохранить</Button>
</template>