<script setup>
    import iconPlay from '@/assets/icon-play.png'
    import iconStop from '@/assets/icon-stop.png'
    import iconPause from '@/assets/icon-pause.png'
    import iconFw from '@/assets/icon-fw.png'
    import iconBw from '@/assets/icon-bw.png'

    const icons = {
        iconPlay,
        iconStop,
        iconPause,
        iconFw,
        iconBw
    }

    const props = defineProps({
        icon: {
            type: String,
            required: true
        }
    })

    const emit = defineEmits(['clickIcon'])

    function iconFunction(icon){
        switch (icon) {
            case 'iconPlay':
                play()
                break

            case 'iconStop':
                stop()
                break
        
            default:
                break;
        }
    }

    function play(){
        console.log('Let\'s play')
        emit('clickIcon')
    }

    function stop(){
        console.log('Please Don\'t stop the music');
    }

</script>

<template>
    <img
        :src="icons[icon]"
        @click="iconFunction(icon)"
        class="icon-player"
        alt="icon"
    >
</template>

<style scoped>
    .icon-player{
        width: 32px;
        cursor: pointer;
    }
        .icon-player:hover {
            filter: invert(90%);
        }
</style>