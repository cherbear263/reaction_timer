<template>
  <div class="bg-cyan-200 w-80 py-4 mx-auto p-2">
    <h1 class="text-xl text-cyan-800 border-b-2 py-1 uppercase font-semibold border-cyan-500 my-4">Results</h1>
    <p>Reaction time: {{ score }}ms</p>
    <p class="text-2xl font-semibold pt-2 text-gray-600 uppercase animate-pulse">{{ rank }}</p>
  </div>
</template>
<script>

export default {
  name: 'Results',
  props: ['score'],
  data() {
    return {
      rank: null
    }
  },
  mounted() {
    if (this.score < 250) {
      this.rank = 'Ninja Fingers'
    } else if (this.score < 400 ) {
      this.rank = 'Rapid Reflexes'
    } else {
      this.rank = 'Snail Pace'
    }
  }

}
</script>
