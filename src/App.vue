<script setup>
  import { ref } from 'vue';
  import Pletina from './components/Pletina.vue'
  import Cassette from '@/assets/cassette.png'
  import CassetteWheel from '@/assets/cassette-wheel.png'
  
  // Tracks ------------------------------------------------------------------------------
  import track01 from '@/assets/music/01. Kavinsky & Lovefoxxx - Nightcall.ogg'
  import track02 from '@/assets/music/02. Desire - Under Your Spell.ogg'
  import track03 from '@/assets/music/03. College - A Real Hero (feat. Electric Youth).ogg'
  import track04 from '@/assets/music/04. Riz Ortolani - Oh My Love (feat. Katyna Ranieri).ogg'
  import track05 from '@/assets/music/05. The Chromatics - Tick of the Clock.ogg'
  import track06 from '@/assets/music/06. Cliff Martinez - Rubber Head.ogg'
  import track07 from '@/assets/music/07. Cliff Martinez - I Drive.ogg'
  import track08 from '@/assets/music/08. Cliff Martinez - He Had a Good Time.ogg'
  import track09 from '@/assets/music/09. Cliff Martinez - They Broke His Pelvis.ogg'
  import track10 from '@/assets/music/10. Cliff Martinez - Kick Your Teeth.ogg'
  import track11 from '@/assets/music/11. Cliff Martinez - Where\'s the Deluxe Version.ogg'
  import track12 from '@/assets/music/12. Cliff Martinez - See You in Four.ogg'
  import track13 from '@/assets/music/13. Cliff Martinez - After The Chase.ogg'
  import track14 from '@/assets/music/14. Cliff Martinez - Hammer.ogg'
  import track15 from '@/assets/music/15. Cliff Martinez - Wrong Floor.ogg'
  import track16 from '@/assets/music/16. Cliff Martinez - Skull Crushing.ogg'
  import track17 from '@/assets/music/17. Cliff Martinez - My Name On a Car.ogg'
  import track18 from '@/assets/music/18. Cliff Martinez - On the Beach.ogg'
  import track19 from '@/assets/music/19. Cliff Martinez - Bride of Deluxe.ogg'
  // End tracks --------------------------------------------------------------------------

  const trackList = [
    track01,
    track02,
    track03,
    track04,
    track05,
    track06,
    track07,
    track08,
    track09,
    track10,
    track11,
    track12,
    track13,
    track14,
    track15,
    track16,
    track17,
    track18,
    track19
  ]

  const tracksTotal = trackList.length - 1
  let trackActual = 0

  const player = ref(null)
  const wheelLeft = ref(null)
  const wheelRight = ref(null)
  const rotate = ref(false)

  function playContent(){
    player.value.play()
    rotate.value = true
  }

  function pauseContent() {
    player.value.pause()
    rotate.value = false
  }

  function stopContent() {
    player.value.pause()
    player.value.currentTime = 0
    rotate.value = false
  }

  function trackNext() {
    if(trackActual < tracksTotal){
      trackActual++
      player.value.src = trackList[trackActual]
      player.value.play()
      rotate.value = true
    }
  }

  function trackPrevious() {
    if(trackActual > 0){
      trackActual--
      player.value.src = trackList[trackActual]
      player.value.play()
      rotate.value = true
    }
  }
</script>

<template>
  <div ref="pletina">
    <div ref="cassette" id="cassette">
      <img :src="Cassette" class="cassette-img">
      <img ref="wheel-left" :src="CassetteWheel" class="wheel-left" :class="{ 'cassette-rotate': rotate }">
      <img ref="wheel-right":src="CassetteWheel" class="wheel-right" :class="{ 'cassette-rotate': rotate }">
    </div>
  </div>
  <audio ref="player">
    <source :src="trackList[trackActual]" type="audio/ogg">
  </audio>

  <div id="pletina">
    <Pletina icon="iconBw" @clickIcon="trackPrevious" />
    <Pletina icon="iconPlay" @clickIcon="playContent" />
    <Pletina icon="iconStop" @clickIcon="stopContent" />
    <Pletina icon="iconPause" @clickIcon="pauseContent" />
    <Pletina icon="iconFw" @clickIcon="trackNext"/>
  </div>
</template>

<style>
  body{
    background-color: #beb4aa;
  }

  #app{
    margin: 5% auto;
    width: 40%;
  }

  #pletina{
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    justify-content: center;
    justify-items: center;
  }

  #cassette{
    position: relative;
    width: 100%;
  }

  .cassette-img {
    width: 100%;
    border: solid 1px;
    border: solid 1px grey;
    border-radius: 8px;
    box-shadow: 0 0 5px black;
  }

  .wheel-left{
    position: absolute;
    bottom: 43.8%;
    left: 24.2%;
  }

  .wheel-right{
    position: absolute;
    bottom: 43.8%;
    left: 63.4%;
  }

  .cassette-rotate {
    animation: spin 2s linear infinite;
  }

  @keyframes spin {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }
</style>
