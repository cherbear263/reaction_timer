<template>
<div class="w-4/5 mx-auto mt-10 text-center">
  <h1 class="text-center text-3xl font-sans font-semibold text-gray-700">Ninja Reaction Timer</h1>
  <button @click="start" :disabled="isPlaying" class="bg-cyan-400 center px-8 py-4 mx-auto my-10 disabled:cursor-not-allowed disabled:bg-gray-400/50 text-white rounded-md hover:bg-cyan-500">play</button>
  <results v-if="showResults" :score="score"/>
  <block v-if="isPlaying" :delay="delay" @end="endGame"/>
</div>
</template>

<style>

</style>

<script>
import Block  from './components/Block.vue'
import Results from './components/Results.vue'
  export default {
    name: 'app',
    data() {
      return {
        isPlaying: false,
        delay: null,
        score: null,
        showResults: false
      }
    },
    components: {
      Block,
      Results
    },
    methods: {
      start() {
        // set the delay to some time between 2 and 7 seconds
        this.delay = 2000 + Math.random() * 5000;
        this.isPlaying = true;   
        this.showResults =  false;     
      },
      endGame(reactionTime) {
        this.score = reactionTime
        this.isPlaying = false
        this.showResults = true
      }
    }
  }
</script>
