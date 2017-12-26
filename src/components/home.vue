<template>
  <div class="hello">
  <ol>
    <li class="pulse1" @touchstart='play(mp3PneumaticTokyo)'>EnV-PneumaticTokyo</li>
    <li class="pulse2" @touchstart='play(mp3rythmC)'>rythmC</li>
  </ol>
    <h1 @touchstart='test'> 
      <span class="swingleft dance-item">{{ msg }}</span>
      <span class="swingright dance-item">{{msg1}}</span>
    </h1>
<!--     <audio controls>
      <source src="~@/assets/EnV-PneumaticTokyo.mp3" type="audio/mpeg">
    </audio> -->
    <img src="~@/assets/Mushroom-1UP.png" class="rythm-bass mr mr1" />
    <img src="~@/assets/Mushroom-1UP.png" class="rythm-medium mr mr2" />
    <img src="~@/assets/Mushroom-1UP.png" class="rythm-bass mr mr3" />
    <img src="~@/assets/Mushroom-1UP.png" class="rythm-high mr-head" />
    <img src="~@/assets/play.png" class="btn-play blur1" :class="{ playing: isPlaying }" @touchstart='play'/>
  </div>
</template>

<script>
import Rythm from 'rythm.js'
import mp3PneumaticTokyo from '@/assets/EnV-PneumaticTokyo.mp3'
import mp3rythmC from '@/assets/rythmC.mp3'
export default {
  name: 'home',
  data () {
    return {
      msg: 'Just',
      msg1: 'Dance',
      rythm: new Rythm(),
      isPlaying: false,
      mp3rythmC:mp3rythmC,
      mp3PneumaticTokyo:mp3PneumaticTokyo
    }
  },
  mounted(){
    // this.rythm = new Rythm();
  },
  methods: {
    test (){
      console.log(1)
    },
    play(music){
      let rythm = this.rythm;
      if(this.isPlaying){
        this.isPlaying = false;
        rythm.stop(true);
        return
      }
      
      rythm.setMusic(music);
      rythm.start();
      this.isPlaying = true;
      rythm.addRythm('swing1', 'swing', 0, 10)
      rythm.addRythm('swing2', 'swing', 0, 10)
      rythm.addRythm('shake1', 'shake', 0, 10)
      rythm.addRythm('jump2', 'jump', 0,10)
      rythm.addRythm('twist2', 'twist', 0, 10, {
                min: 20,
                max: 180
              })
      rythm.addRythm('color3', 'color', 0, 10, {
                from: [255,255,0],
                to:[255,0,0]
              })
      rythm.addRythm('vanish2', 'vanish', 0, 10, {
                reverse: true
              })
      rythm.addRythm('swingleft', 'swing', 0, 10, {
                direction: 'left',
              })
      rythm.addRythm('swingright', 'swing', 0, 10, {
                direction: 'right',
              })
      rythm.addRythm('blur1', 'blur', 0, 10)
      rythm.addRythm('pulse1', 'pulse', 0, 10)
      rythm.addRythm('pulse2', 'pulse', 0, 10, {
              reverse: true,
              min: 0.1,
              max: 1
            })
          

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
  margin: 20px 0;

}
li{
  text-align: left;
}

a {
  color: #42b983;
}
.dance-item{
  display: block;
}
audio{
/*  width: 80%;
  padding-bottom: 50%;
  background: #ccc;*/
}
.btn-play{
  width: 50px;
  margin: 50px;
  transition:all infinite;
}
.mr{
  width: 50px;
  margin: 10px;
}
.mr-head {
  width: 200px;
  margin: 10px auto;
  clear:both;
  display: block;
}
.playing{
  animation: 3s linear 1s infinite normal rotateInfinite;
}

@keyframes rotateInfinite {
  from {
    transform:rotate(0deg);
  }

  to {
    transform:rotate(360deg);
  }
}

</style>
