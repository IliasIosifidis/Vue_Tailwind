<template>
  <div class="w-80 bg-indigo-500 p-12 text-6xl shadow-md shadow-sky-300 text-yellow-400 rounded-xl" v-if="showBlock" @click="stopTimer">
    click me
  </div>
</template>

<script>
export default{
  props: ['delay'],
  data(){
    return {
      showBlock: false,
      timer: null,
      reactionTime: 0
    }
  },
  mounted() {
    setTimeout(() => {
      this.showBlock=true
      this.startTimer()
    }, this.delay)
  },
  methods:{
    startTimer(){
      this.timer = setInterval(() => {
        this.reactionTime += 10
      }, 10)
    },
    stopTimer(){
      clearInterval(this.timer)
      this.$emit('end', this.reactionTime)
    }
  }
}
</script>