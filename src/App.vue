<script setup>
  import { ref } from 'vue';
  import Pletina from './components/Pletina.vue'
  import track01 from '@/assets/track-01.mp3'

  const player = ref(null)

  function playContent(){
    console.log(player.value);
    player.value.play()
    
  }
</script>

<template>
  <audio ref="player">
    <source :src="track01" type="audio/mpeg">
  </audio>
  <Pletina icon="iconBw" @clickIcon="playContent" />
  <Pletina icon="iconPlay" @clickIcon="playContent" />
  <Pletina icon="iconPause" />
  <Pletina icon="iconFw" />
  <Pletina icon="iconStop" />
</template>

<style scoped></style>
