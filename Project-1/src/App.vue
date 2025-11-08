<template>
  <div class="bg-orange-200 h-dvw">
    <h1 class='text-4xl text-center p-6'>Reaction Timer</h1>
    <div class="flex flex-col items-center text-center p-4">
      <button @click="start" :disabled="isPlaying" :class="['w-40 p-4 m-6 text-4xl bg-amber-500 p-3 rounded-2xl shadow-md shadow-yellow-400 focus:shadow-yellow-200 focus:shadow-2xl', isPlaying ? 'cursor-not-allowed opacity-50': 'cursor-pointer']">Play</button>
      <Block v-if="isPlaying" :delay="delay" @end="endGame"/>
      <Results v-if="showResults" :score="score"/>
    </div>
  </div>


</template>

<script>
import Block from './components/Block.vue'
import Results from './components/Results.vue'
export default {
  name:'App',
  components:{ Block, Results },
  data(){
    return {
      isPlaying:false,
      delay: null,
      score: null,
      showResults: false
    }
},
  methods:{
    start(){
      this.delay= 500 + Math.random() * 2500
      this.isPlaying = true
      this.showResults = false
    },
    endGame(reactionTime){
      this.score = reactionTime
      this.isPlaying = false
      this.showResults = true
    }
  }
}
</script>
