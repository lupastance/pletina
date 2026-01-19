<script setup>
    // Importamos todas las imágenes de la pletina
    import iconPlay from '@/assets/icon-play.png'
    import iconStop from '@/assets/icon-stop.png'
    import iconPause from '@/assets/icon-pause.png'
    import iconFw from '@/assets/icon-fw.png'
    import iconBw from '@/assets/icon-bw.png'

    // transformamos cada imagen en una propiedad de un objeto
    // para luego poder acceder más facilmente
    const icons = {
        iconPlay,
        iconStop,
        iconPause,
        iconFw,
        iconBw
    }

    // Definimos las props que el componente puede recibir
    const props = defineProps({
        icon: {
            type: String,
            required: true
        }
    })

    // Definimos los emits que se pueden ejecutar en el componente padre
    const emit = defineEmits(['clickIcon'])
    
</script>

<template>
    <img
        :src="icons[icon]"
        @click="emit('clickIcon')"
        class="icon-player"
        alt="icon"
    >
</template>

<style scoped>
    .icon-player{
        width: 32px;
        cursor: pointer;
        filter: invert(90%);
    }
        .icon-player:hover {
            filter: invert(30%)
        }
</style>