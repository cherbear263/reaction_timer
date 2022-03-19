<template>
  <div class="block w-80 h-40 rounded-md text-white font-semibold text-center bg-cyan-500 center py-11 my-5 mx-auto text-4xl"
  v-if="showBlock"
  @click="stopTimer">
    Click me 
  </div>
</template>
<script>

export default {
  name: 'Block',
  props: ['delay'],
  data() {
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    // when the component is mounted, start counting the delay
    // wehn the delay is reached, set showBlock to True
    setTimeout(() => {
      this.showBlock = true;
      this.startTimer();
    }, this.delay)
  },
  methods: {
    startTimer() {
      // timer increases every 10ms
      this.timer = setInterval(() => {
        this.reactionTime += 10;
      }, 10)

    },
    stopTimer() {
      // stop increasing reactionTime
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)

    }
  }

}
</script>