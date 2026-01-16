<script setup>
  import { ref } from 'vue';
  import Pletina from './components/Pletina.vue'
  import track01 from '@/assets/track-01.mp3'

  const player = ref(null)

  function playContent(){
    player.value.play() 
  }

  function stopContent() {
    player.value.pause()
  }
</script>

<template>
  <audio ref="player">
    <source :src="track01" type="audio/mpeg">
  </audio>
  <Pletina icon="iconBw" @clickIcon="playContent" />
  <Pletina icon="iconPlay" @clickIcon="playContent" />
  <Pletina icon="iconStop" @clickIcon="stopContent" />
  <Pletina icon="iconPause" />
  <Pletina icon="iconFw" />
</template>

<style scoped></style>
