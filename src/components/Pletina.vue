<script setup>
    // Importamos todas las imágenes de la pletina
    import iconPlay from '@/assets/icon-play.png'
    import iconStop from '@/assets/icon-stop.png'
    import iconPause from '@/assets/icon-pause.png'
    import iconFw from '@/assets/icon-fw.png'
    import iconBw from '@/assets/icon-bw.png'
    import button from '@/assets/button.png'

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
    <div id="buttons">
        <img class="icon-player" :src="icons[icon]"/>
        <img
            class="pletina-button"
            :src="button"
            @click="emit('clickIcon')"
            alt="icon"
        >
    </div>
</template>

<style scoped>
    #buttons{
        text-align: center;
    }
    .pletina-button{
        display: block;
        border: solid 1px grey;
        border-radius: 8px;
        box-shadow: 0 0 8px 0 black;
        cursor: pointer;
    }

    .pletina-button:hover {
        filter: invert(10%)
    }

    .icon-player{
        margin: 8px 0;
        width: 16px;
        cursor: pointer;
        filter: invert(20%);
    }
</style>