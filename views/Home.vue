<template>
<div>
    <h1>REACTION TIME APP</h1>
  <button @click="start" :disabled="isPlaying">START</button>
  <Block :delay="delay" v-if="isPlaying" @end="endGame"/>
  <Results v-if="showResults" :score="score"/>
</div>
  
</template>

<script>
import Block from '../components/Block.vue'
import Results from '../components/Results.vue'
export default {
  name: 'Home',
  components: {
    Block,
    Results
  },
  data(){
    return {
      isPlaying:false,
      delay:null,
      score: null,
      showResults: false
    }
  },
  methods:{
    start(){
      this.delay = 2000 + Math.random() * 5000;
      this.isPlaying = true;
    },
      endGame(reactionTime){
      this.showResults= true;
      this.score = reactionTime;
      this.isPlaying = false;
    }
  }

}
  
</script>
