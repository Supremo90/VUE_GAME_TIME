<template>
<div class="block" v-if="showBlock" @click="stopTimer">
     <h1>Block Game</h1>
</div>
</template>
 

<script>

export default {
  name: 'Block',
  props:['delay'],
  data(){
    return{
        showBlock: false,
        timer:null,
        reactionTime:0
    }
  },
  mounted(){
      console.log("MOUNTED");
      setTimeout(() => {
            this.showBlock=true;
            this.startTimer();
            console.log(this.delay);
        }, this.delay);
  },
    updated(){
        console.log("SAVED");
    },
    methods:{
    startTimer(){
        this.timer = setInterval(() => {
            this.reactionTime += 10;
        }, 10)
    },
    stopTimer(){
        clearInterval(this.timer);
        this.$emit('end',this.reactionTime);
        console.log(this.reactionTime);
    }
  }
}

  
</script>

<style lang="scss">
.block {
    width: 400px;
    border-radius: 20px;
    background: rgb(9, 194, 9);
    text-align: center;
    color: white;
    padding: 100px 0;
    margin: 40px auto;
}
</style>
